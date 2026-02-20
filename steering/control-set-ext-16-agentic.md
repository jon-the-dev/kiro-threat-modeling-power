<!-- VERSION_FIXME -->

# Control Set 17: Agentic Security (AGENT)

**Domain**: AGENT - Agent System and Agent-like Component Security
**Version**: 1.0
**Last Updated**: 2026-01-03
**Reference**: OWASP Top 10 for Agentic Applications 2026 (ASI01-ASI10)

---

## Overview

Agentic Security control set, applicable to complete AI Agent systems and agent-like components (Tools, Prompts, Skills). This control set focuses on Agent **behavior, intent, and autonomy** security, forming a complementary relationship with ext-13 (AI/LLM Security):

- **ext-13**: Focuses on LLM model-layer input/output security
- **ext-16**: Focuses on Agent behavior-layer autonomy and collaboration security

**Core Security Paradigm**: Least-Agency Principle
> "Avoid giving agents unnecessary autonomy, not just unnecessary privileges." — OWASP ASI

---

## Trigger Conditions (loaded on demand)

This control set is automatically loaded when the following conditions are detected:

### Complete Agent Systems

- `langchain` / `langgraph` import
- `crewai` / `autogen` / `autogpt` import
- `anthropic.Agent` / `openai.Assistant` API calls
- Agent workflow definition files (`agent.yaml`, `crew.yaml`)

### Agent-like Components

- MCP Server configuration (`mcp.json`, `claude_desktop_config.json`)
- Tool/Function definitions (`tools/*.py`, `functions/*.ts`)
- Skill definitions (`.claude/skills/`, `skills/*.md`)
- Prompt template libraries (`prompts/*.yaml`, `prompt_templates/`)
- Custom Instructions configuration

### Multi-Agent Systems

- A2A (Agent-to-Agent) protocol configuration
- Agent orchestration frameworks (Temporal workflows, Prefect flows)
- Multi-agent communication channels

---

## Core Controls

### AGENT-01: Goal & Intent Protection

**Control Requirement**: Agent goals and intent must be protected against tampering and hijacking

**Applicable Scope**: Agent systems, Prompt templates, Skill definitions

**Control Measures**:

- **Goal Integrity Verification**
  - System prompt integrity verification (hash/signature)
  - Goal definitions must not be overridable by user input
  - Use structured goal definitions instead of free text

- **Intent Alignment Monitoring**
  - Output-to-expected-goal consistency detection
  - Behavioral deviation alerting mechanism
  - Intent reasoning logging

- **Goal Tampering Detection**
  - Detect prompts attempting to modify Agent goals
  - Goal drift detection in multi-turn conversations
  - Indirect goal injection detection (via tool return values)

**Cross-reference**: Complements ext-13 AI-01 (Prompt Injection Prevention)

**OWASP ASI Mapping**: ASI01 - Agent Goal Hijack

---

### AGENT-02: Tool & Skill Governance

**Control Requirement**: Tools and skills available to the Agent must be controlled, auditable, and minimized

**Applicable Scope**: MCP Tools, Function Calling, Skills, Plugins

**Control Measures**:

- **Tool Registration & Verification**
  - Tool source verification and signature validation
  - Tool capability declaration auditing
  - Version management and change tracking
  - Prohibit dynamic loading of unreviewed tools

- **Capability Boundary Restriction**
  - Tool permission allowlist mechanism
  - Resource access scope restriction (file paths, network, API)
  - Operation type restriction (read/write/execute/delete)
  - Call frequency and quota limits

- **Tool Call Chain Auditing**
  - Complete call chain logging
  - Tool parameter recording (sanitized)
  - Call result recording
  - Anomalous call pattern detection

- **MCP Server Security**
  - MCP Server source verification
  - Least privilege configuration
  - Communication encryption (stdio/SSE)
  - Server isolated execution

**Cross-reference**: Complements ext-13 AI-05 (Agent Action Control), ext-12 SUPPLY-04 (Source Verification)

**OWASP ASI Mapping**: ASI02 - Tool Misuse & Exploitation, ASI04 - Agentic Supply Chain

---

### AGENT-03: Non-Human Identity (NHI) Management

**Control Requirement**: Agent and component identities must be explicit, traceable, and privilege-controlled

**Applicable Scope**: Agent service accounts, API credentials, delegation chains

**Control Measures**:

- **Agent Identity Authentication**
  - Unique Agent identifier
  - Secure Agent credential storage
  - Automatic credential rotation
  - Multi-factor authentication (for high-risk operations)

- **Delegation Chain Verification**
  - Complete authorization chain from User to Agent to Tool
  - Delegation scope restriction
  - Delegation time-to-live control
  - Delegation chain audit logging

- **Service Account Least Privilege**
  - Dedicated Agent service accounts
  - Privilege separation by function
  - Prohibit shared credentials
  - Periodic permission review

- **Identity Lifecycle Management**
  - Agent instance creation/destruction records
  - Credential lifecycle management
  - Permission change auditing
  - Stale Agent detection and cleanup

**Cross-reference**: Complements ext-15 CLOUD-01 (IAM Least Privilege), Control-01 (Authentication)

**OWASP ASI Mapping**: ASI03 - Identity & Privilege Abuse

---

### AGENT-04: Memory & Context Security

**Control Requirement**: Agent persistent memory and context must be protected against poisoning and leakage

**Applicable Scope**: Agent Memory, Context Window, Session State, RAG

**Control Measures**:

- **Persistent Memory Protection**
  - Memory storage encryption
  - Memory access control
  - Memory content classification (sensitive/general)
  - Memory version control and rollback

- **Context Poisoning Detection**
  - Detect maliciously injected historical messages
  - Context integrity verification
  - Anomalous context pattern alerting
  - Session history auditing

- **Session Isolation**
  - Strict session isolation between users
  - Context isolation between Agent instances
  - Tenant-level data isolation
  - Cross-session information leakage prevention

- **Memory Cleanup Strategy**
  - Sensitive data automatic expiration
  - User-requested deletion capability
  - Periodic memory review
  - Compliance data retention

**Cross-reference**: Complements ext-13 AI-04 (Data Isolation), Control-10 (Data Protection)

**OWASP ASI Mapping**: ASI06 - Memory & Context Poisoning

---

### AGENT-05: Multi-Agent Communication Security

**Control Requirement**: Inter-Agent communication must be secure, verifiable, and boundary-controlled

**Applicable Scope**: Multi-Agent systems, A2A protocol, Agent orchestration

**Control Measures**:

- **A2A Protocol Security**
  - Inter-Agent communication encryption
  - Message authentication and integrity
  - Replay attack prevention
  - Protocol version compatibility verification

- **Inter-Agent Trust Verification**
  - Agent mutual identity authentication
  - Layered trust levels
  - Trust propagation rules
  - Malicious Agent detection

- **Message Content Security**
  - Message format validation
  - Sensitive data sanitization
  - Message size limits
  - Malicious payload detection

- **Collaboration Boundary Control**
  - Agent collaboration scope restriction
  - Cross-Agent data flow control
  - Collaboration pattern allowlist
  - Collaboration behavior auditing

**Cross-reference**: Complements Control-09 (API Security), ext-11 INFRA-04 (Network Segmentation)

**OWASP ASI Mapping**: ASI07 - Insecure Inter-Agent Communication

---

### AGENT-06: Behavioral Monitoring & Alignment

**Control Requirement**: Agent behavior must be continuously monitored to ensure alignment with expected goals

**Applicable Scope**: All Agent systems and agent-like components

**Control Measures**:

- **Behavioral Deviation Detection**
  - Expected behavior baseline establishment
  - Real-time behavioral deviation analysis
  - Anomalous behavior pattern recognition
  - Behavioral drift trend monitoring

- **Autonomy Boundary Control**
  - Autonomous decision scope restriction
  - Human confirmation for high-risk decisions
  - Dynamic autonomy level adjustment
  - Emergency autonomy downgrade

- **Behavioral Audit Logging**
  - Complete decision process recording
  - Reasoning chain tracing
  - Behavioral attribution analysis
  - Tamper-proof audit logs

- **Rogue Agent Detection**
  - Malicious behavior pattern library
  - Behavioral consistency detection
  - Goal deviation alerting
  - Automatic isolation mechanism

**Cross-reference**: Complements Control-07 (Logging), ext-13 AI-05 (Agent Action Control)

**OWASP ASI Mapping**: ASI10 - Rogue Agents

---

### AGENT-07: Cascading Failure Prevention

**Control Requirement**: Agent systems must have fault isolation and degradation capabilities to prevent cascading failure propagation

**Applicable Scope**: Multi-Agent orchestration, Agent workflows, Tool call chains

**Control Measures**:

- **Fault Isolation**
  - Agent instance-level isolation
  - Tool call failure isolation
  - Error boundary setting
  - Fault domain partitioning

- **Error Propagation Blocking**
  - Error type classification handling
  - Error propagation chain interruption
  - Poisoned input detection
  - Cascade trigger detection

- **Degradation & Circuit Breaking**
  - Service degradation strategy
  - Circuit breaker pattern implementation
  - Graceful degradation paths
  - Degradation state monitoring

- **Orchestration Layer Fault Tolerance**
  - Workflow retry strategy
  - Compensating transaction mechanism
  - Timeout control
  - Deadlock detection and recovery

**Cross-reference**: Complements Control-08 (Error Handling), ext-11 INFRA-03 (Resource Limits)

**OWASP ASI Mapping**: ASI08 - Cascading Failures

---

### AGENT-08: Human-Agent Trust Boundary

**Control Requirement**: A clear human-agent trust boundary must be established; high-risk operations require human confirmation

**Applicable Scope**: All Agent systems

**Control Measures**:

- **Human-in-the-Loop (HITL)**
  - High-risk operations must require human confirmation
  - Confirmation mechanism must not be bypassable
  - Confirmation timeout defaults to rejection
  - Batch confirmation risk control

- **Layered Trust Levels**
  - Operation risk level classification
  - Dynamic trust threshold adjustment
  - User trust level management
  - Context-aware trust assessment

- **Transparency Requirements**
  - Agent behavior must be explainable
  - Decision process must be traceable
  - User informed consent
  - Clear communication of capability boundaries

- **Revocation & Rollback**
  - Operations must be revocable
  - State rollback capability
  - Revocation time limit
  - Revocation audit records

**Cross-reference**: Complements ext-13 AI-05 (Agent Action Control) LLM08 (Excessive Agency)

**OWASP ASI Mapping**: ASI05 - Unexpected Code Execution, ASI09 - Human-Agent Trust Exploitation

---

### AGENT-09: Prompt & Skill Template Security

**Control Requirement**: Prompt templates and Skill definitions must be securely managed to prevent malicious tampering and injection

**Applicable Scope**: Prompt Templates, Skills, Custom Instructions

**Control Measures**:

- **Template Integrity**
  - Template version control
  - Template signature verification
  - Change approval process
  - Template source verification

- **Injection Prevention**
  - Clear variable boundary definitions
  - User input isolation from templates
  - Special character escaping
  - Nested injection detection

- **Skill Security Assessment**
  - Skill capability declaration auditing
  - Skill behavior testing
  - Skill dependency review
  - Skill sandboxed execution

- **Template Access Control**
  - Separate read/write permissions for templates
  - Encrypted storage of sensitive templates
  - Template usage auditing
  - Template leakage detection

**Cross-reference**: Complements ext-13 AI-01 (Prompt Injection Prevention), ext-12 SUPPLY-04 (Source Verification)

**OWASP ASI Mapping**: ASI01 - Agent Goal Hijack (via Prompt), ASI04 - Agentic Supply Chain (Skills)

---

### AGENT-10: Agentic Supply Chain Security

**Control Requirement**: The supply chain for Agent-related components must be secure and controlled

**Applicable Scope**: Agent Frameworks, MCP Servers, Tools, Skills, Plugins

**Control Measures**:

- **Framework Security**
  - Agent framework vulnerability monitoring
  - Framework version management
  - Timely security patch application
  - Framework configuration auditing

- **MCP Server Supply Chain**
  - MCP Server source verification
  - Server code review
  - Dependency scanning
  - Malicious Server detection

- **Tool/Skill Supply Chain**
  - Tool source allowlist
  - Skill publisher verification
  - Code signature verification
  - Malicious code scanning

- **Third-Party Integration Security**
  - Third-party service security assessment
  - API credential security management
  - Integration point monitoring
  - Data flow security

**Cross-reference**: Fully complements ext-12 (Supply Chain Security)

**OWASP ASI Mapping**: ASI04 - Agentic Supply Chain Vulnerabilities

---

## Control Applicability Matrix

| Control | Agent System | MCP Tools | Skills | Prompts | Multi-Agent |
|---------|:----------:|:---------:|:------:|:-------:|:-----------:|
| AGENT-01 | ● | ○ | ● | ● | ● |
| AGENT-02 | ● | ● | ● | ○ | ● |
| AGENT-03 | ● | ● | ○ | ○ | ● |
| AGENT-04 | ● | ○ | ○ | ○ | ● |
| AGENT-05 | ● | ○ | ○ | ○ | ● |
| AGENT-06 | ● | ○ | ● | ○ | ● |
| AGENT-07 | ● | ○ | ○ | ○ | ● |
| AGENT-08 | ● | ● | ● | ○ | ● |
| AGENT-09 | ○ | ○ | ● | ● | ○ |
| AGENT-10 | ● | ● | ● | ○ | ● |

**Legend**: ● Strongly related | ○ Weakly related or on-demand

---

## L4 References

Detailed practice guides are available in the `references/` directory:

- reference-set-17-agentic-security.md
- reference-set-17-mcp-security.md
- reference-set-17-multi-agent-patterns.md
- reference-set-17-skill-security.md

Internal references:

- agentic-threats.yaml
- llm-threats.yaml (cross-reference)

External references:

- OWASP Top 10 for Agentic Applications 2026
- OWASP Non-Human Identities (NHI) Top 10
- MITRE ATLAS (Adversarial Threat Landscape for AI Systems)

---

## STRIDE Mapping

| STRIDE | Applicable Controls | Threat Examples |
|--------|---------------------|-----------------|
| S | AGENT-03, AGENT-05 | Agent identity spoofing, A2A message spoofing |
| T | AGENT-01, AGENT-04, AGENT-09 | Goal tampering, memory poisoning, template injection |
| R | AGENT-06, AGENT-08 | Untraceable behavior, unauditable operations |
| I | AGENT-04, AGENT-05 | Memory leakage, inter-Agent data leakage |
| D | AGENT-07 | Cascading failures causing service unavailability |
| E | AGENT-01, AGENT-02, AGENT-06 | Goal hijack privilege escalation, tool abuse, Rogue Agent |

---

## Relationship with ext-13 (AI/LLM Security)

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    Security Control Layer Relationship                   │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                          │
│  Application Layer                                                       │
│  ┌─────────────────────────────────────────────────────────────────┐   │
│  │  ext-16: Agentic Security (AGENT)                                │   │
│  │  ───────────────────────────────────────────────────────────    │   │
│  │  • Agent behavior and intent security                            │   │
│  │  • Tool/Skill governance                                         │   │
│  │  • Multi-Agent collaboration security                            │   │
│  │  • Human-Agent trust boundary                                    │   │
│  └─────────────────────────────────────────────────────────────────┘   │
│                              │ Depends on                               │
│                              ▼                                          │
│  Model Layer                                                             │
│  ┌─────────────────────────────────────────────────────────────────┐   │
│  │  ext-13: AI/LLM Security (AI)                                    │   │
│  │  ───────────────────────────────────────────────────────────    │   │
│  │  • Prompt injection prevention                                   │   │
│  │  • Output validation                                             │   │
│  │  • Model access control                                          │   │
│  │  • Data isolation                                                │   │
│  └─────────────────────────────────────────────────────────────────┘   │
│                                                                          │
│  Relationship: ext-16 EXTENDS ext-13 (Agent builds on LLM)              │
│  Cross-references: AGENT-01↔AI-01, AGENT-02↔AI-05, AGENT-04↔AI-04      │
│                                                                          │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## Version History

| Version | Date | Changes |
|---------|------|---------|
| 1.0 | 2026-01-03 | Initial release based on OWASP Agentic Top 10 2026 |
