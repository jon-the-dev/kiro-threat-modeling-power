# Usage Guide

## Quick Start

Open your project in Kiro IDE and use natural language to invoke the threat modeling power.

## Basic Usage

### Complete Threat Model

The simplest way to start:

```
Perform a complete threat model analysis on this repository
```

Kiro will automatically:

1. Execute all 8 phases sequentially
2. Generate comprehensive reports
3. Create POCs and attack paths
4. Provide mitigation recommendations

### With Project Context

Provide context for better analysis:

```
Analyze this codebase for security threats

Project context:
- E-commerce platform backend API
- Django REST Framework with PostgreSQL
- Handles PII and payment data
- Deployed on AWS ECS

Focus areas: Authentication, payment flow, API security, data protection
```

## Advanced Usage

### With Flags

#### Debug Mode

Get internal YAML data files and evaluation reports:

```
Perform threat modeling on this repository with debug mode enabled
```

This publishes:

- All phase YAML data files
- Knowledge base query logs
- Coverage validation reports
- Evaluation metrics

#### Language Selection

Generate reports in different languages:

```
Analyze this project for security threats in Chinese
```

Supported languages:

- English (en) - default
- Chinese (zh)
- Japanese (ja)
- Korean (ko)
- Spanish (es)
- French (fr)
- German (de)
- Portuguese (pt)
- Russian (ru)

#### Detailed Reports

Generate per-vulnerability detailed analysis:

```
Perform threat modeling with detailed risk reports enabled
```

This creates individual analysis files for each validated risk in `Risk_Assessment_Report/detailed/`

#### Combined Flags

```
Analyze this repository with debug mode, detailed reports, and Chinese output
```

## Usage Modes

### Mode 1: Complete Workflow (Standard)

Full 8-phase threat modeling:

```
Perform complete threat model analysis on this repository

Project context:
- Microservices architecture
- Node.js + Express + MongoDB
- OAuth2 authentication
- Kubernetes deployment

Focus: Service mesh security, API gateway, inter-service communication
```

### Mode 2: Knowledge Base Consultation

Query security knowledge without full analysis:

```
Query complete information for CWE-89 (SQL Injection), including attack patterns, testing methods, and mitigations
```

Response includes:

- CWE overview and description
- Related CAPEC attack patterns
- WSTG testing procedures
- ASVS requirements
- Mitigation examples with code

### Mode 3: Deep Vulnerability Analysis

Analyze specific code for vulnerabilities:

```
Analyze SSRF risk in this code and construct attack path:

[paste code snippet]
```

Response includes:

- Vulnerability mechanism explanation
- Attack path construction
- POC design
- CWE/CAPEC/ATT&CK mapping
- Remediation recommendations

### Mode 4: Security Test Generation

Generate test cases based on security standards:

```
Generate WSTG-based security test cases for this API endpoint:

[paste API specification or code]
```

Response includes:

- Authentication test cases
- Authorization test cases
- Input validation tests
- Session management tests
- Test payloads and expected results

### Mode 5: Forward Integration (Design Phase)

Threat modeling during design phase:

```
Conduct STRIDE threat analysis based on this API specification:

[paste OpenAPI/Swagger specification]
```

Response includes:

- DFD generated from API endpoints
- Trust boundaries identified
- STRIDE threat enumeration
- Design-phase recommendations

### Mode 6: Backward Integration (Penetration Testing)

Support for active penetration testing:

```
I found JWT signature verification bypass in the target system, help construct complete attack chain
```

Response includes:

- Vulnerability confirmation
- Complete attack chain steps
- POC payload generation
- ATT&CK technique mapping
- Report template

## Scenario-Based Examples

### Scenario 1: New Project Security Review

```
Perform comprehensive security assessment on this new project

Project details:
- FastAPI backend with React frontend
- PostgreSQL database
- Redis for caching
- JWT authentication
- Deployed on AWS Lambda + API Gateway

This is a pre-launch security review. Focus on:
1. Authentication and authorization
2. API security
3. Data protection
4. Cloud security configuration
```

### Scenario 2: AI/LLM Application Security

```
Analyze this AI application for security threats

Project details:
- LangChain-based RAG system
- OpenAI GPT-4 integration
- Vector database (Pinecone)
- User document upload and processing
- Agent with tool calling capabilities

Focus on:
1. Prompt injection risks
2. Data leakage through embeddings
3. Agent tool security
4. PII handling in prompts
```

### Scenario 3: Legacy System Audit

```
Perform security audit on this legacy system

Project details:
- Monolithic PHP application (10+ years old)
- MySQL database
- Mixed authentication (sessions + basic auth)
- No modern security controls
- Planning migration to microservices

Focus on:
1. Critical vulnerabilities
2. Technical debt security impact
3. Migration security considerations
```

### Scenario 4: Compliance Assessment

```
Assess this application against OWASP ASVS Level 2 requirements

Project details:
- Healthcare data processing system
- HIPAA compliance required
- .NET Core backend
- SQL Server database

Generate compliance gap analysis and remediation roadmap
```

### Scenario 5: Specific Vulnerability Investigation

```
Investigate potential SQL injection vulnerability in this code:

[paste code]

Provide:
1. Vulnerability confirmation
2. Exploitation POC
3. Attack path analysis
4. Remediation code
5. Test cases
```

## Understanding the Output

### Report Structure

After analysis completes, you'll find reports in `Risk_Assessment_Report/`:

```
Risk_Assessment_Report/
├── {PROJECT}-RISK-ASSESSMENT-REPORT.md    # Main report (read this first)
├── {PROJECT}-RISK-INVENTORY.md            # All validated risks
├── {PROJECT}-MITIGATION-MEASURES.md       # How to fix issues
├── {PROJECT}-PENETRATION-TEST-PLAN.md     # Test cases
├── P1-PROJECT-UNDERSTANDING.md            # Phase reports (audit trail)
├── P2-DFD-ANALYSIS.md
├── P3-TRUST-BOUNDARY.md
├── P4-SECURITY-DESIGN-REVIEW.md
├── P5-STRIDE-THREATS.md
├── P6-RISK-VALIDATION.md
└── P7-MITIGATION-PLANNING.md
```

### Main Report Sections

The main report contains 10 sections:

1. **Risk Posture Overview** - Top-10 risks, STRIDE heatmap, key metrics
2. **Executive Summary** - 10 key findings, immediate actions
3. **System Architecture** - Modules, dependencies, entry points
4. **Security Design Assessment** - 16 domain scorecard
5. **STRIDE Threat Analysis** - Complete threat enumeration
6. **Risk Validation & POC** - Validated risks with POCs
7. **Attack Path Analysis** - Attack chains with diagrams
8. **Threat Priority Matrix** - Risk prioritization
9. **Mitigation Recommendations** - Remediation plans with code
10. **Compliance Mapping** - Framework coverage

### Risk Severity Levels

Risks are categorized by priority:

- **P0 (Critical)** - Fix immediately (0-24 hours)
- **P1 (High)** - Fix within 7 days
- **P2 (Medium)** - Fix within 30 days
- **P3 (Low)** - Backlog

## Working with Results

### Reviewing Risks

Start with the Risk Inventory:

```
Open Risk_Assessment_Report/{PROJECT}-RISK-INVENTORY.md
```

Each risk includes:

- Unique ID (VR-001, VR-002, etc.)
- CVSS score
- STRIDE categories
- CWE references
- Affected modules
- Threat references
- Mitigation links

### Implementing Fixes

Use the Mitigation Measures report:

```
Open Risk_Assessment_Report/{PROJECT}-MITIGATION-MEASURES.md
```

Each mitigation includes:

- Risk references
- Priority level
- Difficulty assessment
- Effort estimate
- Before/after code examples
- Implementation steps
- Verification methods

### Running Tests

Use the Penetration Test Plan:

```
Open Risk_Assessment_Report/{PROJECT}-PENETRATION-TEST-PLAN.md
```

Each test case includes:

- Attack path reference
- Prerequisites
- Exploitation steps
- Expected results
- Verification methods
- Required tools

## Tips for Best Results

### 1. Provide Context

The more context you provide, the better the analysis:

```
Good: "Django REST API handling payment data with JWT auth"
Better: "Django 4.2 REST API with Stripe integration, JWT auth, PostgreSQL, deployed on AWS ECS"
```

### 2. Specify Focus Areas

Guide the analysis to your concerns:

```
Focus on: Authentication, payment processing, PII handling, API rate limiting
```

### 3. Include Architecture Details

Mention key architectural decisions:

```
Architecture:
- Microservices with service mesh (Istio)
- Event-driven with Kafka
- Multi-tenant with row-level security
- Zero-trust network model
```

### 4. Mention Compliance Requirements

If you have compliance needs:

```
Compliance requirements: PCI-DSS, SOC 2, GDPR
```

### 5. Use Debug Mode for Learning

Enable debug mode to see how the analysis works:

```
Analyze with debug mode to see internal analysis process
```

## Troubleshooting

### "Phase X failed to complete"

Check the phase report in `.phase_working/{SESSION_ID}/reports/` for details.

### "Knowledge base query failed"

Verify the KB is accessible:

```bash
cd ~/.kiro/powers/threat-modeling
./kb --stride spoofing
```

### "Module discovery returned no results"

Ensure you're in the project root directory with source code.

### "Reports not generated"

Check that all 8 phases completed successfully. Review session metadata in `.phase_working/{SESSION_ID}/_session_meta.yaml`

## Next Steps

- Review [POWER.md](POWER.md) for detailed capabilities
- Check [INSTALLATION.md](INSTALLATION.md) for setup issues
- See [README.md](README.md) for complete documentation
