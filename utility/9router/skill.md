## 安装9router

[[DB] No SQLite driver available (better-sqlite3 + sql.js both failed) · Issue #987 · decolua/9router](https://github.com/decolua/9router/issues/987)

## 导入Cursor配置

[9router/src/app/api/oauth/cursor/auto-import/route.js at master · decolua/9router](https://github.com/decolua/9router/blob/master/src/app/api/oauth/cursor/auto-import/route.js)

如果自动导入失败，用SQLite3连接位于`~/.config/Cursor/User/globalStorage/state.vscdb`的数据库文件，在`ItemTable`中查找`cursorAuth/accessToken`和`storage.serviceMachineId`手动粘贴