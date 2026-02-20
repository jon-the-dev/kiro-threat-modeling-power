---
name: threat-modeling
version: 1.0.0
description: AI-native automated software risk analysis using STRIDE methodology
author: jon-the-dev
---

# Threat Modeling Power

**Version**: 1.0.0 (based on v3.0.3 threat-modeling-skill)  

## Overview

AI-native automated software risk analysis power. LLM-driven, Code-First approach for comprehensive security risk assessment, threat modeling, security analysis, and penetration testing using the STRIDE methodology.

## What This Power Does

This power performs deep security analysis on your codebase through an 8-phase workflow. **Each phase should be delegated to a subagent to save context and enable parallel processing.**

### Execution Strategy

**IMPORTANT**: Use subagents for each phase to avoid context overflow:

```
For each phase 1-8:
  1. Delegate phase to subagent with phase-specific instructions
  2. Wait for subagent completion
  3. Review subagent output
  4. Proceed to next phase
```

### 8-Phase Workflow

1. **Phase 1: Project Understanding** - Discovers architecture, modules, entry points
   - Delegate to subagent with: "Analyze project structure, identify modules, entry points, and tech stack"
   
2. **Phase 2: DFD Analysis** - Maps data flows and system interactions
   - Delegate to subagent with: "Create data flow diagrams, identify all data flows and system interactions"
   
3. **Phase 3: Trust Boundary Evaluation** - Identifies security boundaries
   - Delegate to subagent with: "Identify and evaluate trust boundaries, privilege levels, and security zones"
   
4. **Phase 4: Security Design Review** - Assesses 16 security domains
   - Delegate to subagent with: "Review security design across authentication, authorization, input validation, cryptography, etc."
   
5. **Phase 5: STRIDE Threat Analysis** - Enumerates threats using STRIDE methodology
   - Delegate to subagent with: "Perform STRIDE threat enumeration for all components and data flows"
   
6. **Phase 6: Risk Validation** - Validates risks with POCs and attack paths
   - Delegate to subagent with: "Validate identified risks, create POCs and attack path diagrams"
   
7. **Phase 7: Mitigation Planning** - Generates actionable remediation plans
   - Delegate to subagent with: "Create mitigation plans with code examples and implementation guidance"
   
8. **Phase 8: Report Generation** - Creates comprehensive security reports
   - Delegate to subagent with: "Generate final reports: risk assessment, inventory, mitigations, and pentest plan"

## Key Features

- **Comprehensive Coverage**: 16 security domains, 107 controls
- **Threat Intelligence**: STRIDE→CWE→CAPEC→ATT&CK mapping (26+ MB knowledge base)
- **Automated Discovery**: Python scripts for module and entry point detection
- **POC Generation**: Creates proof-of-concept exploits for validated risks
- **Attack Path Analysis**: Visualizes attack chains with Mermaid diagrams
- **Compliance Mapping**: Maps to OWASP, NIST, ISO 27001, PCI-DSS, and more
- **Multi-Language Support**: Reports in EN, ZH, JA, KO, ES, FR, DE, PT, RU

## When to Use

- Pre-release security assessment
- Security audit of existing applications
- Penetration testing preparation
- Compliance requirement validation
- Architecture security review
- AI/LLM application security analysis

## Supported Project Types

- Web APIs (REST, GraphQL, gRPC)
- Microservices architectures
- AI/LLM applications (RAG, agents, model endpoints)
- Mobile backends
- Cloud-native applications
- Legacy systems

## Quick Start

```
Perform a complete threat model analysis on this repository
```

Or with options:

```
Perform threat modeling with debug mode enabled and Chinese output
```

## Output

The power generates a comprehensive report package in `Risk_Assessment_Report/`:

### Required Reports (4)

1. **RISK-ASSESSMENT-REPORT.md** - Main synthesis report (10 sections)
2. **RISK-INVENTORY.md** - Complete validated risks with POCs
3. **MITIGATION-MEASURES.md** - Remediation plans with code examples
4. **PENETRATION-TEST-PLAN.md** - Test cases mapped to attack paths

### Phase Reports (7)

- P1 through P7 working documents for audit trail

### Optional Outputs

- **Detailed Risk Reports** - Per-vulnerability deep analysis (with --detailed flag)
- **HTML Reports** - Web-viewable versions of all reports

## Flags

- `--debug` - Publish internal YAML data files and evaluation reports
- `--lang=xx` - Set output language (en, zh, ja, ko, es, fr, de, pt, ru)
- `--detailed` - Generate detailed per-risk analysis reports

## When to Load Steering Files

Load specific steering files based on your workflow:

- **Authentication issues** → `control-set-01-authentication.md`, `reference-set-01-password-storage.md`, `reference-set-01-session-management.md`
- **Authorization/access control** → `control-set-02-authorization.md`, `reference-set-02-authorization.md`, `reference-set-02-idor-prevention.md`
- **Input validation/injection** → `control-set-03-input-validation.md`, `reference-set-03-injection-prevention.md`, `reference-set-03-sql-injection-prevention.md`
- **XSS/client-side security** → `control-set-05-client-side.md`, `reference-set-05-xss-prevention.md`, `reference-set-05-csrf-prevention.md`, `reference-set-05-csp.md`
- **Cryptography** → `control-set-06-cryptography.md`, `reference-set-06-cryptographic-storage.md`, `reference-set-06-tls.md`
- **API security** → `control-set-09-api-security.md`, `reference-set-09-rest-security.md`, `reference-set-09-graphql.md`
- **Cloud/infrastructure** → `control-set-ext-11-infrastructure.md`, `reference-set-ext-11-kubernetes-security.md`, `reference-set-ext-11-docker-security.md`
- **AI/LLM security** → `control-set-ext-13-ai-llm.md`, `reference-set-ext-13-ai-agent-security.md`
- **Supply chain/dependencies** → `control-set-ext-12-supply-chain.md`, `reference-set-ext-12-dependency-management.md`

## Knowledge Base

The power includes 94 security control and reference documents covering:

- **Security Controls**: 16 domains, 107 controls
- **OWASP References**: 73 detailed implementation guides
- **AI/LLM Threats**: 350+ AI-specific threat patterns
- **Compliance**: OWASP ASVS, WSTG, MASTG, NIST, ISO 27001
- **CVE Database**: 323K+ vulnerabilities with CWE mappings

## Requirements

- Python 3.10+
- SQLite3
- Python packages: pyyaml (installed via pipenv)

## Architecture

This power uses a strict 8-phase FSM (Finite State Machine) workflow where each phase:

1. Reads structured YAML data from previous phase
2. Performs analysis using knowledge base queries
3. Writes YAML data file (machine-readable)
4. Writes Markdown report (human-readable)
5. Validates output before proceeding

Data flows through YAML files only - Markdown reports are for documentation, not data extraction.

## Examples

### Complete Assessment

```
Analyze @. for security threats

Project context:
- E-commerce platform backend API
- Django REST Framework
- Handles PII and payment data

Focus: Authentication, payment flow, API security
```

### Specific Vulnerability Analysis

```
Analyze SSRF risk in this code and construct attack path:
[paste code snippet]
```

### Design Phase Analysis

```
Conduct STRIDE threat analysis on this API specification:
[paste OpenAPI spec]
```

## Credits

Based on the threat-modeling skill by jon-the-dev:
<https://github.com/jon-the-dev/kiro-threat-modeling-power>

Adapted for Kiro Powers architecture.
