---
title: Threat Modeling Workflow
inclusion: manual
keywords: threat modeling, security assessment, stride, risk analysis, penetration testing
---

# Threat Modeling Power - Workflow Guide

You are executing the Threat Modeling Power, an AI-native automated security risk analysis system using STRIDE methodology.

## Core Principles

1. **Strict Sequential Execution**: 8 phases must execute in order (P1→P2→P3→P4→P5→P6→P7→P8)
2. **Data via YAML**: Structured data flows through YAML files, Markdown is for reports only
3. **Knowledge-Driven**: Query the knowledge base (26+ MB) for every threat, risk, and mitigation
4. **No Mock Data**: All analysis must be based on real code evidence
5. **Complete Coverage**: Every phase must be fully executed, no shortcuts

## 8-Phase Workflow

```
P1: Project Understanding → P2: DFD Analysis → P3: Trust Boundaries → P4: Security Design
    ↓                           ↓                   ↓                      ↓
P5: STRIDE Threats → P6: Risk Validation → P7: Mitigation Planning → P8: Report Generation
```

### Phase Execution Protocol

For each phase:

1. **Read** previous phase YAML data (except P1)
2. **Execute** 4-Gate protocol: THINKING → PLANNING → EXECUTING → REFLECTING
3. **Write** YAML data file (PRIMARY output)
4. **Write** Markdown report (SECONDARY output)
5. **Validate** output completeness
6. **Proceed** to next phase only after validation passes

## Output Structure

All outputs go to `Risk_Assessment_Report/` in the target repository:

```
Risk_Assessment_Report/
├── {PROJECT}-RISK-ASSESSMENT-REPORT.md    # Main synthesis (10 sections)
├── {PROJECT}-RISK-INVENTORY.md            # All validated risks
├── {PROJECT}-MITIGATION-MEASURES.md       # Remediation plans
├── {PROJECT}-PENETRATION-TEST-PLAN.md     # Test cases
├── P1-PROJECT-UNDERSTANDING.md            # Phase reports
├── P2-DFD-ANALYSIS.md
├── P3-TRUST-BOUNDARY.md
├── P4-SECURITY-DESIGN-REVIEW.md
├── P5-STRIDE-THREATS.md
├── P6-RISK-VALIDATION.md
├── P7-MITIGATION-PLANNING.md
└── .phase_working/{SESSION_ID}/           # Working data (YAML files)
    ├── data/
    │   ├── P1_project_context.yaml
    │   ├── P2_dfd_elements.yaml
    │   └── ... (P3-P8 YAML files)
    └── reports/
        └── (working reports during execution)
```

## Session Management

Each execution creates a session: `{PROJECT_NAME}_{YYYYMMDD_HHMMSS}`

Session metadata tracks:

- Current phase status
- Data file locations
- Validation results
- Timestamps

## Knowledge Base Queries

Use the `kb` wrapper script for all knowledge queries:

```bash
# Get SKILL_PATH
SKILL_PATH=$(pwd)

# STRIDE queries
$SKILL_PATH/kb --stride spoofing
$SKILL_PATH/kb --stride-controls S

# CWE/CAPEC chains
$SKILL_PATH/kb --cwe CWE-89
$SKILL_PATH/kb --full-chain CWE-89

# Attack patterns
$SKILL_PATH/kb --capec CAPEC-66
$SKILL_PATH/kb --attack-technique T1078

# Verification tests
$SKILL_PATH/kb --stride-tests S
$SKILL_PATH/kb --wstg-category ATHN

# AI/LLM threats
$SKILL_PATH/kb --all-llm
```

## Flags

- `--debug`: Publish internal YAML data files and evaluation reports
- `--lang=xx`: Set output language (en, zh, ja, ko, es, fr, de, pt, ru)
- `--detailed`: Generate detailed per-risk analysis reports after P8

## Key Constraints

### Absolute Prohibitions

- ❌ NO MOCK DATA - All analysis must be based on real code
- ❌ NO SIMPLIFIED IMPLEMENTATIONS - Each phase must be fully executed
- ❌ NO BYPASSING PROBLEMS - Must diagnose root cause when blocked

### Data Flow Rules

- ❌ FORBIDDEN: Reading .md files for data extraction
- ❌ FORBIDDEN: Embedding YAML blocks inside .md as data source
- ✅ REQUIRED: Data flows via .yaml files only
- ✅ REQUIRED: YAML written FIRST, then Markdown report

### Phase Isolation

- Each phase is independent execution unit
- No phase skipping (violates FSM invariant)
- No parallel phase execution (data dependencies)
- Validation must pass before proceeding

## STRIDE Methodology

### STRIDE Categories

| Category | Threat | Security Property |
|----------|--------|-------------------|
| **S** | Spoofing | Authentication |
| **T** | Tampering | Integrity |
| **R** | Repudiation | Non-repudiation |
| **I** | Information Disclosure | Confidentiality |
| **D** | Denial of Service | Availability |
| **E** | Elevation of Privilege | Authorization |

### STRIDE per Element Matrix

| Element Type | S | T | R | I | D | E |
|--------------|---|---|---|---|---|---|
| Process      | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| Data Store   |   | ✓ | ✓ | ✓ | ✓ |   |
| Data Flow    |   | ✓ |   | ✓ | ✓ |   |
| External Entity | ✓ |   | ✓ |   |   |   |

## Security Domains (16)

### Core Domains (10)

1. AUTHN - Authentication
2. AUTHZ - Authorization
3. INPUT - Input Validation
4. OUTPUT - Output Encoding
5. CLIENT - Client-Side Security
6. CRYPTO - Cryptography
7. LOG - Logging & Monitoring
8. ERROR - Error Handling
9. API - API Security
10. DATA - Data Protection

### Extended Domains (6)

11. INFRA - Infrastructure Security
2. SUPPLY - Supply Chain Security
3. AI - AI/LLM Security
4. MOBILE - Mobile Security
5. CLOUD - Cloud Security
6. AGENT - Agentic Security

## Threat Intelligence Chain

```
STRIDE → CWE → CAPEC → ATT&CK → CVE → KEV
  ↓       ↓      ↓        ↓       ↓      ↓
Category Weakness Attack  Technique Vuln  Exploited
```

## Error Recovery

If a phase fails:

1. Check `.phase_working/{SESSION_ID}/_session_meta.yaml`
2. Find last completed phase
3. Load that phase's YAML data
4. Resume from next phase

## Validation Gates

Each phase has validation rules:

- **BLOCKING**: Must pass to proceed
- **WARNING**: Acknowledge and continue

Common validations:

- YAML file exists and is valid
- Required fields present
- Data consistency (e.g., count conservation P5→P6)
- ID format correctness

## Reference Files

All phase instructions are in `phases/P{1-8}-*.md`

- Read the specific phase file when executing that phase
- Follow the 4-Gate protocol defined in each phase
- Use the knowledge base queries as specified

## Success Criteria

Threat modeling is complete when:

- All 8 phases executed successfully
- All required reports generated
- Main report has all 10 sections
- P6 POCs and P7 mitigations included completely
- Validation passed for all phases
