# 认识工具

## 认识mujoco

[(80 封私信 / 32 条消息) 几个常见机器人仿真软件的比较（详细版） - 知乎](https://zhuanlan.zhihu.com/p/12193176654)

## 认识RoboCup 3D比赛环境

[RoboCup Simulation / RCSSServerMJ · GitLab](https://gitlab.com/robocup-sim/rcssservermj)

## 认识mjlab任务

[mjlab · PyPI](https://pypi.org/project/mjlab/)

[如何新增一个 G1 RL 任务（从 0 到可训练） — mjlab Documentation](https://www.nagi.fun/mjlab-homierl/source/walkthrough/how_to_add_g1_task.html)

mjlab和isaac lab管理任务的机制类似，`train.py`和`play.py`会`import mjlab.tasks`导入内置任务。教程让我们clone源码来使用mjlab，并把自己的任务写进`src/mjlab/tasks/<your_task>/`，我认为大可不必，完全可以在自己的脚本导入自己的`tasks`。毕竟，什么项目都clone源码来改的习惯很不好，不是所有项目都需要大改。

# 工具链安装

## 安装mujoco

[(79 封私信 / 26 条消息) 如何在ubuntu20.04安装mujoco - 知乎](https://zhuanlan.zhihu.com/p/535806578)

pip正常安装即可，可执行程序叫`python -m mujoco.viewer`

conda下安装用`mamba install mujoco`可执行程序叫`mujoco-simulate`

# mjlab package

[MJLab与IsaacLab_RL运控教学文档 - Robotics Tutorial](http://robotics-tutorial.dmbot.cn/05_%E8%BF%90%E5%8A%A8%E6%8E%A7%E5%88%B6/40_%E4%BB%BF%E7%9C%9F/MJLab%E4%B8%8EIsaacLab_RL%E8%BF%90%E6%8E%A7%E6%95%99%E5%AD%A6%E6%96%87%E6%A1%A3/#mjlab)

## 从 mjlab 到 mjlab tasks

### 1. Python entry point 入口点注册

`pyproject.toml` 中注册了：

`[project.entry-points."mjlab.tasks"] mjlab_playground = "mjlab_playground"`

这是一个名为 `mjlab.tasks` 的 **entry point group**。当你的包被 `pip install` 后，Python 的包元数据中会记录：

- `mjlab_playground` 这个包属于 `mjlab.tasks` 组。

**所有主流包管理器都支持** **Python 标准打包规范**（[PEP 621](https://peps.python.org/pep-0621/#entry-points) / [PEP 345](https://peps.python.org/pep-0345/)），entry point 机制本身是 Python 标准库 `importlib.metadata` 提供的。

| 方式  | 配置位置 |
| --- | --- |
| `pip install .` | `pyproject.toml` `[project.entry-points]`（或旧式 `setup.cfg`） |
| `poetry` | `pyproject.toml` `[tool.poetry.plugins]` |
| `pdm` | `pyproject.toml` `[project.entry-points]` |
| `flit` | `pyproject.toml` `[project.entry-points]` |
| `pip install -e .` | 同上（可编辑安装也有效） |

只要包被 **安装**（install），entry point 就会被写入 `.dist-info/entry_points.txt`。mjlab 启动时调用 `importlib.metadata.entry_points()` 就是从这些 `.dist-info` 元数据文件中读的。

### 2. mjlab 自动发现与导入项目

mjlab 在启动时（`mjlab/**init**.py:34-46`）执行：

`def _import_registered_packages() -> None: mjlab_tasks = entry_points().select(group="mjlab.tasks") for entry_point in mjlab_tasks: entry_point.load()`

`entry_points().select(group="mjlab.tasks")` 会

- 找到所有声明了 `mjlab.tasks` 入口点的包，然后 `.load()` 会 import 它们（例如 `mjlab_playground`）。

### 3. 从项目路由到 tasks

`mjlab_playground/**init**.py` 被触发，里面的 `from ... import *` 会把所有子任务的配置类导入，从而注册到 gymnasium 环境中。

## 从 tasks 到 task

- `config` 一类task的机器人型号列表
  - `g1` 机器人型号例如Unitree G1
    - `__init__.py` register_mjlab_task 注册 + 命令行入口
    - `env_cfg.py` ManagerBasedRLEnvCfg
    - `rl_cfg.py` RslRlOnPolicyRunnerCfg
- `mdp` 根据isaaclab的官方文档，这里存放不同管理器config所需要的函数，但实际上也会存放需要的子config
- `_env_cfg.py` 可能存在一个额外的基类用于存放不限型号的配置

## 从 task 到 Scene

## 从 task 到 Managers

### Observation

观察管理器根据组织成组的多个terms计算观察值。每个项都可以应用噪声、削波、缩放、延迟和历史。组可以选择将它们的项连接成一个张量。

观察组：将多个观察term捆绑在一起。组通常用于区分不同目的的观察结果（例如，“参与者”代表参与者，“评论家”代表价值函数）——应该就是把太长的观测空间向量分类。

### Action

动作管理器聚合多个动作项，每个动作项控制模拟的不同实体或方面。它拆分策略的动作张量，并将每个切片路由到适当的动作项。

### Reward: 制定“奖惩制度”

将总奖励计算为加权奖励terms的总和。奖励terms是从一个嵌套的配置类中解析出来的，该类包含奖励管理器的设置和奖励terms配置。

### Command: 指定“运动目标”

用于为代理生成要执行的命令。它使在同一环境中切换不同的命令生成策略变得方便。例如，

- 在由四足机器人组成的环境中，对它的命令可以是速度命令或位置命令。
- 人形机器人行走的目标速度或目标位置
- 人形机器人踢球的目标角度和目标力度

### Event: 施加“规则怪谈”

事件管理器在不同的模拟事件中触发操作：启动（初始化时一次）、重置（在事件重置时）或间隔（在模拟过程中定期）。常见用途包括域随机化和状态重置。例如，

- 在初始化/重置时改变物体的质量或摩擦系数
- 施加随机以固定步长间隔向机器人施加推力
- 随机移动操作物体例如足球的位置让机器人寻找

### Termination: 判断“是否要停”

终止管理器聚合多个终止terms以计算事件完成信号（也称为dones）。

terms可以是truncations（时间超时）或terminations（故障发生）。

将环境作为参数，根据各个终止条件的并集（逻辑或），返回一个形状为（num_envs，）的布尔张量，确定每个env是否应该终止。

### Curriculum: 设置“可变脚本”

在训练期间根据代理性能更新环境参数。每个term可以修改任务难度的不同方面（例如，地形复杂性、指挥范围）。

随着agent的改进，这些有助于通过逐步增加学习任务的难度来稳定学习。

## 从 tasks 到 environment script

[任务设计工作流程 — Isaac Lab 文档](https://docs.robotsfan.com/isaaclab_v1/source/overview/core-concepts/task_workflows.html)

[创建基于管理器的强化学习环境 — Isaac Lab 文档](https://docs.robotsfan.com/isaaclab_v1/source/tutorials/03_envs/create_manager_rl_env.html#tutorial-create-manager-rl-env)

step