---
title: Career Conversations
emoji: "\U0001F4AC"
colorFrom: blue
colorTo: indigo
sdk: gradio
sdk_version: "5.29.1"
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

1. Create a virtual environment:
   `uv venv`
2. Activate it:
   `source .venv/bin/activate`
3. Install dependencies:
   `uv pip install -r requirements.txt`
4. Add required environment variables in `.env`:
   - `OPENAI_API_KEY`
   - `PUSHOVER_TOKEN`
   - `PUSHOVER_USER`
5. Start the app:
   `python app.py`

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
