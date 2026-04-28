---
on:
  workflow_dispatch:

permissions:
  contents: read
  pull-requests: read
  issues: read

engine:
  id: codex
  model: openai/gpt-4o
  env:
    OPENAI_BASE_URL: "https://openrouter.ai/api/v1"
    OPENAI_API_KEY: ${{ secrets.OPENROUTER_API_KEY }}

network:
  allowed:
    - defaults
    - openrouter.ai

safe-outputs:
  create-pull-request:
    title-prefix: "[agentic-app] "
    allowed-files:
      - "README.md"
      - "requirements.txt"
      - "package.json"
      - "src/**"
      - "app/**"
      - "components/**"
      - "pages/**"
      - "public/**"
      - "tests/**"
    max: 1
---

# Build Application Using OpenRouter

You are an AI coding agent. Build a simple application based on this repository.

## Goal

Create a starter web application that demonstrates how to call OpenRouter API securely from the backend.

## Requirements

1. Create a minimal backend API endpoint.
2. The backend should call OpenRouter using an environment variable.
3. Do not expose the API key to frontend code.
4. Add clear setup instructions in README.md.
5. Add example `.env.example`.
6. Add basic error handling.
7. Create a pull request with the implementation.

## Suggested Stack

Use Node.js / Express or another lightweight stack if the repository already uses a different framework.

## Security

Never commit real API keys.
Use environment variables only.