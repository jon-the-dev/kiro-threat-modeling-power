<!-- VERSION_FIXME -->

# Control Set 14: AI/LLM Security (AI)

**Domain**: AI - AI/LLM Security
**Version**: 1.0
**Last Updated**: 2025-12-30

---

## Overview

AI/LLM security control set, applicable to large language model and AI Agent applications. Loaded on demand when the following trigger conditions are detected:

- openai API calls
- anthropic API calls
- langchain/llamaindex imports
- Local model loading (transformers/llama.cpp)

---

## Core Controls

### AI-01: Prompt Injection Prevention

**Control Requirement**: Prompt injection attacks must be defended against

- Isolate user input from system prompts
- Input sanitization and escaping
- Use structured prompt templates
- Detect and block injection attempts

### AI-02: Output Validation

**Control Requirement**: LLM output must be validated before use

- Output format validation (JSON Schema)
- Sensitive information filtering
- Sandbox validation before code execution
- Hallucination detection and flagging

### AI-03: Model Access Control

**Control Requirement**: Model access must be controlled

- Secure API key storage and rotation
- Rate limiting to prevent abuse
- User-level access control
- Audit logging for all calls

### AI-04: Data Isolation

**Control Requirement**: Sensitive data must not be leaked to models

- PII must be anonymized before sending
- Sensitive data detection in context windows
- Prohibit training data containing sensitive information
- Data classification and labeling

### AI-05: Agent Action Control

**Control Requirement**: AI Agent actions must be restricted

- Action allowlist mechanism
- Human confirmation for high-risk operations
- Resource access scope restrictions
- Rollback and undo capabilities

### AI-06: Model Security

**Control Requirement**: The model itself must be secure

- Model file integrity verification
- Prevent model theft/extraction
- Adversarial example protection
- Model version management

---

## L4 References

Detailed practice guides are available in the `references/` directory:

- reference-set-14-ai-agent-security.md
- reference-set-14-prompt-injection-prevention.md

Internal references:

- llm-threats.yaml

---

## STRIDE Mapping

| STRIDE | Applicable Controls |
|--------|---------------------|
| S | AI-03 |
| T | AI-01, AI-05 |
| R | AI-03 |
| I | AI-02, AI-04, AI-06 |
| D | AI-03 |
| E | AI-05 |
