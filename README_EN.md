# Xiaocai Campus Assistant · NUFE Edition

A campus assistant demo adapted for Nanjing University of Finance and Economics, built with Next.js, FastAPI, and SQLite.

[中文说明](README.md)

## Features

Campus knowledge, streaming AI conversations, conversation history, recent tasks, submission receipts, administrator review, and study resources. Public access mode separates browser visitor identities.

AI requires a configured model provider. This demo is not connected to the university's live academic, authentication, or booking systems. Historical course reviews do not establish current assessment arrangements.

## Run on the existing Windows computer

```powershell
cd D:\zafu_xiaolin_current_review
npm run dev
```

Open http://localhost:3000 and keep the terminal running. Run commands in the project directory containing `package.json`, not a Windows system directory.

## First-time setup

With Node.js/npm, Python, and access to the private repository:

```powershell
git clone https://github.com/unsaoh/xiaocai-campus-assistant.git
cd xiaocai-campus-assistant
npm install
npm --prefix frontend/my-app install
python -m pip install -r fastapi/requirements.txt
```

Copy `fastapi/.env.example` to `fastapi/.env` only if no configuration exists. Configure model names, provider credentials, endpoint, and independent random secrets. Then run `npm run dev` on Windows. Other systems can start the [backend](fastapi/README.md) and [frontend](frontend/my-app/README.md) separately.

## Deployment and limitations

GitHub hosts the source; it does not run the complete application. Backend and database hosting are separate. Temporary demo URLs may expire and depend on the local computer remaining online. See [deployment instructions](DEPLOYMENT.md).

Secrets, local databases, logs, and user uploads are excluded. Ollama is not yet installed. Remaining work includes Agent mode entry, cancellation when switching conversations, tool event consistency, anonymous rate limiting, and some homepage descriptions.

## Attribution

Adapted from the **Nonglin XiaoLin** campus AI Agent framework. Original [Chinese](docs/upstream/README.md) and [English](docs/upstream/README_EN.md) documentation is archived for attribution, not as a description of this edition's capabilities. Legacy sample data and compatibility paths retain their original meaning.
