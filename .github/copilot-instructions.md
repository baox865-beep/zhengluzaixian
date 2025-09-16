# Copilot Instructions for AI Agents

## 项目架构与核心知识

- **单体 Express 应用**：所有 HTTP 路由集中于 `index.js`，无多层目录或复杂拆分。主业务为计数器 API，演示 Node.js + MySQL 的最小可用云托管后端。
- **数据库集成**：`db.js` 用 Sequelize 连接 MySQL，模型 `Counter` 自动同步表结构。数据库连接依赖环境变量 `MYSQL_USERNAME`、`MYSQL_PASSWORD`、`MYSQL_ADDRESS`，本地需手动配置，云端自动注入。
- **前端交互**：`index.html` 通过 AJAX 调用 `/api/count`，展示和操作计数。
- **云托管部署**：`Dockerfile`、`container.config.json` 支持一键部署，自动创建数据库（见 `executeSQLs` 字段）。

## 关键文件与职责

- `index.js`：应用入口，定义所有 API 路由、服务启动、日志与中间件。
- `db.js`：Sequelize 初始化与模型定义，负责数据库连接和表结构管理。
- `index.html`：前端页面，演示计数器功能及 API 调用方式。
- `Dockerfile`、`container.config.json`：云托管/容器部署配置。
- `package.json`：依赖与启动脚本（`npm start`）。

## 主要开发与调试流程

- **本地开发**：
	- 需本地 MySQL，设置环境变量后 `npm start` 启动。
	- 推荐用 VSCode `launch.json` 的“运行脚本: start”配置调试。
- **云托管部署**：
	- 依赖 `Dockerfile` 和 `container.config.json`，无需手动构建镜像。
	- 云端环境变量需在控制台补全，否则数据库连接失败。

## 项目约定与模式

- API 返回统一结构：`{ code, data }`。
- 计数器自增：POST `/api/count`，参数 `{ action: "inc" }`；清零：`{ action: "clear" }`。
- 日志采用 `morgan`（tiny 格式），跨域支持已开启（`cors`）。
- 仅与 MySQL 集成，无外部 API 调用。

## 依赖与集成点

- 主要依赖：`express`、`sequelize`、`mysql2`、`cors`、`morgan`。
- 云托管自动创建数据库（见 `container.config.json` 的 `executeSQLs`）。

## 典型扩展与修改建议

- 扩展业务建议以 `index.js` 为主入口，按需拆分路由与服务。
- 参考 `README.md` 获取 API 示例与环境变量说明。
- 如需自定义数据库表结构，修改 `db.js` 并同步。

---

如需补充更详细的开发约定、调试技巧或集成说明，请在此文档下方补充。
