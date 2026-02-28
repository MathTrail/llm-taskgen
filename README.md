# mathtrail-llm-taskgen
LLM connector that generates personalized math olympiad problems using language models.

## Mission & Responsibilities
- Accept generation parameters (topic, difficulty, constraints)
- Construct prompts for LLM (problem text, hints, solution)
- Call LLM API (OpenAI, Anthropic, or local model)
- Parse and validate LLM output (structured JSON)
- Return well-formed task objects to Task Service

## Tech Stack
- **Language**: Go or Python (TBD based on LLM SDK availability)
- **LLM**: OpenAI API / Anthropic API / local Ollama
- **Events**: HTTP service invocation (sync)

## API & Communication
- **Inbound**: HTTP service invocation from mathtrail-task
- **Outbound**: External LLM API calls (OpenAI, Anthropic)

## Data Persistence
- **None** — stateless generator. May cache prompts in Redis (future).

## Secrets
- `LLM_API_KEY` — OpenAI / Anthropic API key
- Vault path: `secret/data/{env}/mathtrail-llm-taskgen/`

## Infrastructure
Standard `infra/` layout:
- `infra/helm/` — Helm chart + environment overlays (dev, on-prem, cloud)
- `infra/terraform/` — Environment scaffolds (stateless — no DB)
- `infra/ansible/` — On-prem node preparation

## Roadmap
1. Define prompt templates for math problem generation (structured output)
2. Implement LLM API client with retry and fallback
3. Add output validation (ensure problem has solution, hints, difficulty metadata)
