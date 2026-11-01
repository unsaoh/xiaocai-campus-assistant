# 小财校园助手 · 南财版后端

FastAPI 后端，为小财网页端与小程序提供 AI 对话、访客身份、知识查询、投稿审核和学习资料接口，使用 SQLite 保存数据。

## 启动

Windows 推荐在项目根目录执行 `npm run dev`，详见[项目说明](../README.md)。单独运行后端时，在项目根目录安装依赖：

```text
python -m pip install -r fastapi/requirements.txt
```

首次使用时复制 `fastapi/.env.example` 为 `fastapi/.env`，配置模型服务和独立随机密钥；已有配置不要覆盖。然后在项目根目录运行：

```text
python -m uvicorn app.main:app --reload --host 127.0.0.1 --port 8001 --app-dir fastapi
```

API 地址为 http://localhost:8001。启用 `ENABLE_API_DOCS` 时可访问 `/docs` 查看实际路由。

数据库启动时自动建表，默认文件为 `fastapi/demo.db`；`DATABASE_URL` 可覆盖路径。管理员审核需要单独配置管理员账号，新部署不包含原电脑聊天记录和上传资料。

## 目录

- `app/api/`：API 路由。
- `app/agent/`：任务规划、工具选择、执行与回复生成。
- `app/services/`：模型调用和业务服务。
- `app/skills/`：知识库与工具能力定义。
- `app/db/`：数据模型与数据库会话。
- `app/tests/`：功能测试。

旧框架的课程、通知和场地示例不代表真实南财系统接入。
