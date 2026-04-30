---
title: Career Conversations
emoji: "\U0001F4AC"
colorFrom: blue
colorTo: indigo
sdk: gradio
sdk_version: "5.49.1"
app_file: app.py
pinned: false
---

## Career Conversations

This project is a personal career chat assistant built with Gradio.

It runs a conversational interface that answers questions about my background using:
- a short written profile in `me/summary.txt`
- parsed content from `me/linkedin.pdf`

The app also supports simple lead capture and follow-up logging:
- when someone shares contact details, it records them
- when a question cannot be answered, it logs that question for later review

Both of those events are sent through Pushover notifications.

## Tech Stack

- Python 3.12
- Gradio UI
- OpenAI Chat Completions API
- `pypdf` for reading LinkedIn PDF content
- GitHub Actions for deployment
- Hugging Face Spaces for hosting

## Running Locally

1. Install dependencies and create the environment:
   `uv sync`
2. Add required environment variables in `.env`:
   - `OPENAI_API_KEY`
   - `PUSHOVER_TOKEN`
   - `PUSHOVER_USER`
3. Run the app:
   `uv run app.py`

If you are setting up from scratch and want the full dependency workflow:

1. `uv sync`
2. `uv run python --version`
3. `uv run python -c "import gradio; print(gradio.__version__)"`

This project is currently pinned to Gradio 5.x to match the chatbot code path used in `app.py`.

## Deployment

This repository deploys to a Hugging Face Space from GitHub Actions on pushes to `main`.

Workflow file:
- `.github/workflows/deploy-huggingface-space.yml`

GitHub secret required for deploy:
- `HF_TOKEN`

Runtime secrets (set in Hugging Face Space settings):
- `OPENAI_API_KEY`
- `PUSHOVER_TOKEN`
- `PUSHOVER_USER`
