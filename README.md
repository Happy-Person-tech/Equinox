# Al-Khaytal

A professional, fully-interactive web app that decodes Emirati heritage — the
traditional Bedouin weaving craft of *Al-Sadu* — using a four-agent LangGraph RAG
pipeline with a human-in-the-loop review gate.

## What it is

Al-Khaytal answers questions about UAE heritage by running a multi-agent pipeline
that researches, verifies, and publishes a citable report with a generated
illustration. A human review step sits in the middle so nothing is published until
you approve it.

- **FastAPI backend** (`server.py`) — wraps the agent pipeline and streams live
  stage updates to the browser over Server-Sent Events.
- **Single-page frontend** (`static/`) — a dark neon theme with a sidebar, four
  navigable pages, and a live animated pipeline visualisation. Plain HTML/CSS/JS —
  no Node, no build step.

## The agent pipeline

| Agent | Role |
|-------|------|
| Historian | Retrieves grounded facts from the heritage knowledge base |
| Verifier | Checks sources and scores factual reliability |
| Curator | Drafts the initial report |
| Publisher | Finalises the report and generates the illustration |

Between Curator and Publisher the workflow **pauses for human review** (HITL) —
you review the draft and facts, then approve or send feedback.

## Pages

| Page | What it does |
|------|--------------|
| **Home** | Hero, feature cards, and a static pipeline overview |
| **Decode** | Ask a question → watch the pipeline run live → review the draft → approve → get a citable report + illustration |
| **Artifact Lab** | Train the model on artefact images, then identify new ones |
| **About** | Architecture, data isolation, and known limits |

## Tech stack

- Python 3.13+, FastAPI, Uvicorn
- LangGraph + LangChain + Chroma (RAG)
- Server-Sent Events (SSE) for live updates
- Vanilla HTML/CSS/JS frontend

## Prerequisites

- Python 3.13 or newer
- An OpenRouter API key (or any OpenAI-compatible key)

