# agent-chat-ui-docker

Docker image of [agent-chat-ui](https://github.com/langchain-ai/agent-chat-ui) for the
[Muffin](https://github.com/gururafiki/muffin) agent, built for **ARM64** (Oracle Cloud A1).

The Dockerfile clones upstream agent-chat-ui and builds it. It uses the **same-origin API proxy**:
`NEXT_PUBLIC_API_URL` defaults to `/api`, but is baked to an **absolute** URL in CI (the LangGraph
SDK does `new URL(apiUrl)`, which rejects relative paths). Set repo variable
`PUBLIC_API_URL = https://muffin.rafiki.guru/api`. At runtime the Next server proxies to
`LANGGRAPH_API_URL` (set by `muffin-deployment` in the docker stack).

CI builds + pushes `ghcr.io/gururafiki/agent-chat-ui-docker:latest` (native arm64 runner).
