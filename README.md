# 小财校园助手 · 南财版

面向南京财经大学校园信息查询与学习交流的 AI 助手演示项目，采用 Next.js + FastAPI + SQLite。

[English](README_EN.md) · [部署说明](DEPLOYMENT.md) · [访客身份说明](docs/VISITOR_ACCESS.md)

## 当前功能

| 功能 | 说明 |
| --- | --- |
| 校园知识库 | 学生手册题库、宿舍、校园设施、社团和历史课程评价 |
| AI 助手 | 流式对话与历史会话，需要配置可用的模型 API |
| 最近任务 | 首页展示当前访客的近期非空会话，可继续查看 |
| 内容投稿 | 提交后取得回执编号，查询待审核、通过或拒绝状态 |
| 审核后台 | 管理员审核投稿，需要单独配置管理员账号 |
| 学习资料 | 资料列表与文件访问；新部署不包含本机上传资料 |
| 访客隔离 | 免登录模式按浏览器访客身份区分聊天记录 |

本项目尚未接入学校真实教务、统一身份认证和场地预约系统。课程评价来自历史整理资料，不保证当前学期考核安排。Agent 编排仍在完善，旧框架的课程、通知和场地示例不能视为真实校园服务。

## 在当前 Windows 电脑上打开

打开 PowerShell，先进入项目目录，再启动：

```powershell
cd D:\zafu_xiaolin_current_review
npm run dev
```

启动成功后打开 **http://localhost:3000**。保持终端窗口开启，按 `Ctrl+C` 停止。

若提示找不到 `package.json`，请确认终端位于项目根目录，而不是 Windows 系统目录。执行 `Test-Path package.json` 应返回 `True`。

## 新电脑首次运行

先安装 Node.js/npm 和兼容项目依赖的 Python 环境，取得私有仓库访问权限后运行：

```powershell
git clone https://github.com/unsaoh/xiaocai-campus-assistant.git
cd xiaocai-campus-assistant
npm install
npm --prefix frontend/my-app install
python -m pip install -r fastapi/requirements.txt
```

首次运行时将 `fastapi/.env.example` 复制为 `fastapi/.env`（已有配置不要覆盖）。填写模型名称、对应服务商密钥和服务地址，将安全相关占位值替换为独立随机值。不要提交真实 `.env`。

随后在项目根目录执行 `npm run dev`。根目录启动脚本适用于 Windows，同时运行前端 3000 端口与后端 8001 端口。Linux/macOS 可按[前端说明](frontend/my-app/README.md)和[后端说明](fastapi/README.md)分别启动。

数据库启动时自动建表，默认文件为 `fastapi/demo.db`，可通过 `DATABASE_URL` 修改。

## 目录

```text
frontend/my-app/   网页前端
fastapi/app/       API、模型调用、知识库与数据服务
miniprogram/      微信小程序客户端
docs/             部署、访问与内容管理说明
tools/            本地演示及资料整理工具
```

## 部署与限制

- GitHub 用于查看和管理代码，不会自动运行完整网站；后端、数据库和模型服务仍需部署。
- `localhost:3000` 指向访问者自己的电脑。老师从外网访问需要公网服务或临时转发。
- [临时演示说明](docs/TEACHER_DEMO.md)中的域名可能失效，临时转发依赖电脑持续开机和联网。
- 仓库排除了密钥、聊天数据库、日志和用户上传资料；新部署需要重新配置和添加资料。
- 本地 Ollama 尚未部署完成，AI 依赖配置的模型服务。
- 待完善：Agent 入口模式、会话切换时取消旧请求、工具执行事件字段、匿名调用限流和部分首页说明。
