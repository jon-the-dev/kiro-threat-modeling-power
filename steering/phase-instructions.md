---
title: Phase Execution Instructions
inclusion: auto
---

# Threat Modeling Phase Execution

When executing threat modeling, you must follow the 8-phase workflow strictly.

## 4-Gate Protocol (Every Phase)

Each phase follows this internal state machine:

### 1. THINKING Gate

- Understand the phase objective
- Review upstream data dependencies
- Identify unknowns and risks
- Output: THINKING section with problem statement

### 2. PLANNING Gate

- Decompose into sub-tasks
- Identify required tools/scripts
- Define expected outputs
- Output: PLANNING section with task table

### 3. EXECUTING Gate

- Execute each sub-task sequentially
- Write YAML data file FIRST
- Write Markdown report SECOND
- Use knowledge base queries as needed

### 4. REFLECTING Gate

- Verify all outputs created
- Check data completeness
- Validate against phase requirements
- Output: REFLECTION section with checklist

## Phase-Specific Instructions

Detailed instructions for each phase are in:

- `phases/P1-PROJECT-UNDERSTANDING.md`
- `phases/P2-DFD-ANALYSIS.md`
- `phases/P3-TRUST-BOUNDARY.md`
- `phases/P4-SECURITY-DESIGN-REVIEW.md`
- `phases/P5-STRIDE-ANALYSIS.md`
- `phases/P6-RISK-VALIDATION.md`
- `phases/P7-MITIGATION-PLANNING.md`
- `phases/P8-REPORT-GENERATION.md`

Read the appropriate phase file when executing that phase.

## Script Usage

### Module Discovery (Phase 1)

```bash
python scripts/module_discovery.py . --p1-discovery --output-yaml > \
  .phase_working/{SESSION_ID}/data/P1_static_discovery.yaml
```

### Knowledge Base Queries (Phase 5, 6, 7)

```bash
# STRIDE threats
python scripts/unified_kb_query.py --stride spoofing

# CWE details with full chain
python scripts/unified_kb_query.py --cwe CWE-89 --full-chain

# CAPEC attack patterns
python scripts/unified_kb_query.py --capec CAPEC-66 --attack-chain

# Mitigations
python scripts/unified_kb_query.py --cwe CWE-89 --mitigations
```

### Phase Validation

```bash
python scripts/phase_data.py --validate --phase {N} --root .
```

## Data Model

### Entity ID Formats

- Module: `M-{Seq:03d}` (e.g., M-001)
- Finding: `F-P{N}-{Seq:03d}` (e.g., F-P1-001)
- Gap: `GAP-{Seq:03d}` (e.g., GAP-001)
- Threat: `T-{STRIDE}-{Element}-{Seq}` (e.g., T-S-P001-001)
- Validated Risk: `VR-{Seq:03d}` (e.g., VR-001)
- Mitigation: `MIT-{Seq:03d}` (e.g., MIT-001)
- POC: `POC-{Seq:03d}` (e.g., POC-001)
- Attack Path: `AP-{Seq:03d}` (e.g., AP-001)
- Attack Chain: `AC-{Seq:03d}` (e.g., AC-001)
- Test Case: `TC-{Seq:03d}` (e.g., TC-001)

### DFD Element IDs

- External Interactor: `EI-{NNN}` (e.g., EI-001)
- Process: `P-{NNN}` (e.g., P-001)
- Data Store: `DS-{NNN}` (e.g., DS-001)
- Data Flow: `DF-{NNN}` (e.g., DF-001)
- Trust Boundary: `TB-{NNN}` (e.g., TB-001)

## Critical Rules

1. **YAML First**: Always write YAML data file before Markdown report
2. **No Mock Data**: All analysis based on actual code evidence
3. **Complete Execution**: No simplified or partial implementations
4. **Knowledge Queries**: Query KB for every threat, risk, mitigation
5. **Count Conservation**: P5 threat count = P6 (verified + theoretical + pending + excluded)
6. **Validation Gates**: Must pass before proceeding to next phase

## Output Locations

- YAML Data: `.phase_working/{SESSION_ID}/data/P{N}_*.yaml`
- MD Reports: `.phase_working/{SESSION_ID}/reports/P{N}-*.md`
- Final Reports: `Risk_Assessment_Report/{PROJECT}-*.md`
- Phase Reports: `Risk_Assessment_Report/P{N}-*.md`

## Session ID Format

`{PROJECT_NAME}_{YYYYMMDD_HHMMSS}`

Example: `MYAPP_20260216_143022`
