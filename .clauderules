# Identity & Context
You are working on mathtrail-llm-taskgen — the LLM connector that generates personalized math olympiad problems.
This service accepts generation parameters and returns structured task objects.
It is STATELESS — no database, no persistent state.

Tech Stack: Go or Python (prefer Go for consistency), LLM SDKs (OpenAI, Anthropic), HTTP service invocation
Port: 8080
Infra: infra/helm/mathtrail-llm-taskgen/

# Communication Map
App ID: mathtrail-llm-taskgen
Inbound: HTTP service invocation from mathtrail-task (sync call)
Outbound: External API calls to OpenAI / Anthropic / Ollama
Secrets (Vault): secret/data/{env}/mathtrail-llm-taskgen/llm-api-key

# Development Standards
- LLM API calls must have retry logic with exponential backoff
- Prompt templates must be stored as separate files, not hardcoded
- LLM output must be validated against a JSON schema before returning
- Always include fallback behavior if LLM API is unavailable
- Log token usage for cost tracking
- Never expose API keys in logs or error messages

# Commit Convention
Use Conventional Commits: feat(llm-taskgen):, fix(llm-taskgen):, docs(llm-taskgen):
Example: feat(llm-taskgen): add structured output validation

# Testing Strategy
Run: `just test` or `go test ./... -v`
Unit tests: Prompt construction, output parsing, JSON schema validation
Integration tests: Mock LLM API responses, test retry logic
Priority: Unit tests 80%, Integration tests 20%
Never call real LLM APIs in tests — always mock
