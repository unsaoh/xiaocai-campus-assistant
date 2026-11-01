# 小财校园助手 · 南财版前端

Next.js 网页客户端，包含工作台、AI 聊天、校园知识库、投稿回执和学习资料页面。

推荐按[项目说明](../../README.md)启动前后端，在当前 Windows 电脑执行：

```powershell
cd D:\zafu_xiaolin_current_review
npm run dev
```

单独启动前端时，在本目录执行 `npm install` 和 `npm run dev`，并确保后端已运行。访问 http://localhost:3000。

未设置 `NEXT_PUBLIC_API_BASE_URL` 时使用同源 API 路径，由 Next.js 转发至 `API_PROXY_TARGET`（默认 `http://localhost:8001`）。生产部署需同时运行后端。

页面源码位于 `src/app/`；网页标题位于 `src/app/layout.tsx`。部署说明见 [DEPLOYMENT.md](../../DEPLOYMENT.md)。
