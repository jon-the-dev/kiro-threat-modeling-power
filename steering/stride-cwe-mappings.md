# STRIDE-CWE Mappings

This document provides comprehensive mappings between STRIDE threat categories and Common Weakness Enumeration (CWE) identifiers, along with associated CAPEC attack patterns and mitigation strategies.

## Spoofing

**Description Keywords:** authentication, identity, credential, impersonat, spoof

### Primary CWEs

| CWE ID | Name | Abstraction |
|--------|------|-------------|
| CWE-287 | Improper Authentication | Class |
| CWE-306 | Missing Authentication for Critical Function | Base |
| CWE-295 | Improper Certificate Validation | Base |
| CWE-290 | Authentication Bypass by Spoofing | Base |
| CWE-798 | Use of Hard-coded Credentials | Base |
| CWE-522 | Insufficiently Protected Credentials | Class |
| CWE-640 | Weak Password Recovery Mechanism for Forgotten Password | Base |
| CWE-1390 | Weak Authentication | Class |
| CWE-294 | Authentication Bypass by Capture-replay | Base |
| CWE-307 | Improper Restriction of Excessive Authentication Attempts | Base |
| CWE-521 | Weak Password Requirements | Base |
| CWE-520 | .NET Misconfiguration: Use of Impersonation | Variant |
| CWE-556 | ASP.NET Misconfiguration: Use of Identity Impersonation | Variant |
| CWE-645 | Overly Restrictive Account Lockout Mechanism | Base |
| CWE-836 | Use of Password Hash Instead of Password for Authentication | Base |

### Related CWEs

| CWE ID | Name |
|--------|------|
| CWE-1037 | Processor Optimization Removal or Modification of Security-critical Code |
| CWE-1244 | Internal Asset Exposed to Unsafe Debug Access Level or State |
| CWE-1273 | Device Unlock Credential Sharing |
| CWE-257 | Storing Passwords in a Recoverable Format |
| CWE-370 | Missing Check for Certificate Revocation after Initial Check |
| CWE-488 | Exposure of Data Element to Wrong Session |
| CWE-614 | Sensitive Cookie in HTTPS Session Without 'Secure' Attribute |

### CAPEC Attack Patterns

| CAPEC ID | Name | Severity | Attack Techniques |
|----------|------|----------|-------------------|
| CAPEC-112 | Brute Force | High | T1110 - Brute Force |
| CAPEC-114 | Authentication Abuse | Medium | T1548 - Abuse Elevation Control Mechanism |
| CAPEC-115 | Authentication Bypass | Medium | T1548 - Abuse Elevation Control Mechanism |
| CAPEC-12 | Choosing Message Identifier | High | - |
| CAPEC-151 | Identity Spoofing | Medium | - |
| CAPEC-166 | Force the System to Reset Values | Medium | - |
| CAPEC-194 | Fake the Source of Data | Medium | - |
| CAPEC-196 | Session Credential Falsification through Forging | Medium | T1134.002, T1134.003, T1606 |
| CAPEC-2 | Inducing Account Lockout | Medium | T1531 - Account Access Removal |
| CAPEC-21 | Exploitation of Trusted Identifiers | High | T1134, T1528, T1539 |

## Tampering

**Description Keywords:** integrity, tamper, modif, inject, manipulat

### Primary CWEs

| CWE ID | Name | Abstraction |
|--------|------|-------------|
| CWE-354 | Improper Validation of Integrity Check Value | Base |
| CWE-924 | Improper Enforcement of Message Integrity During Transmission in a Communication Channel | Base |
| CWE-352 | Cross-Site Request Forgery (CSRF) | Compound |
| CWE-345 | Insufficient Verification of Data Authenticity | Class |
| CWE-494 | Download of Code Without Integrity Check | Base |
| CWE-346 | Origin Validation Error | Class |
| CWE-347 | Improper Verification of Cryptographic Signature | Base |
| CWE-353 | Missing Support for Integrity Check | Base |
| CWE-649 | Reliance on Obfuscation or Encryption of Security-Relevant Inputs without Integrity Checking | Base |
| CWE-89 | Improper Neutralization of Special Elements used in an SQL Command ('SQL Injection') | Base |
| CWE-94 | Improper Control of Generation of Code ('Code Injection') | Base |
| CWE-129 | Improper Validation of Array Index | Variant |
| CWE-360 | Trust of System Event Data | Base |
| CWE-77 | Improper Neutralization of Special Elements used in a Command ('Command Injection') | Class |
| CWE-915 | Improperly Controlled Modification of Dynamically-Determined Object Attributes | Base |

### Related CWEs

| CWE ID | Name |
|--------|------|
| CWE-1191 | On-Chip Debug and Test Interface With Improper Access Control |
| CWE-319 | Cleartext Transmission of Sensitive Information |
| CWE-1004 | Sensitive Cookie Without 'HttpOnly' Flag |
| CWE-5 | J2EE Misconfiguration: Data Transmission Without Encryption |
| CWE-590 | Free of Memory not on the Heap |
| CWE-593 | Authentication Bypass: OpenSSL CTX Object Modified after SSL Objects are Created |
| CWE-732 | Incorrect Permission Assignment for Critical Resource |
| CWE-798 | Use of Hard-coded Credentials |
| CWE-822 | Untrusted Pointer Dereference |
| CWE-825 | Expired Pointer Dereference |

### CAPEC Attack Patterns

| CAPEC ID | Name | Severity | Attack Techniques |
|----------|------|----------|-------------------|
| CAPEC-100 | Overflow Buffers | Very High | - |
| CAPEC-111 | JSON Hijacking (aka JavaScript Hijacking) | High | - |
| CAPEC-126 | Path Traversal | Very High | - |
| CAPEC-135 | Format String Injection | High | - |
| CAPEC-136 | LDAP Injection | High | - |
| CAPEC-141 | Cache Poisoning | High | T1557.002 - Adversary-in-the-Middle: ARP Cache Poisoning |
| CAPEC-148 | Content Spoofing | Medium | T1491 - Defacement |
| CAPEC-15 | Command Delimiters | High | - |
| CAPEC-160 | Exploit Script-Based APIs | Medium | - |
| CAPEC-183 | IMAP/SMTP Command Injection | Medium | - |

## Repudiation

**Description Keywords:** log, audit, trace, repudiat, accountability

### Primary CWEs

| CWE ID | Name | Abstraction |
|--------|------|-------------|
| CWE-778 | Insufficient Logging | Base |
| CWE-943 | Improper Neutralization of Special Elements in Data Query Logic | Class |
| CWE-1115 | Source Code Element without Standard Prologue | Base |
| CWE-117 | Improper Output Neutralization for Logs | Base |
| CWE-1245 | Improper Finite State Machines (FSMs) in Hardware Logic | Base |
| CWE-1248 | Semiconductor Defects in Hardware Logic with Security-Sensitive Implications | Base |
| CWE-1254 | Incorrect Comparison Logic Granularity | Base |
| CWE-1255 | Comparison Logic is Vulnerable to Power Side-Channel Attacks | Variant |
| CWE-1264 | Hardware Logic with Insecure De-Synchronization between Control and Data Channels | Base |
| CWE-511 | Logic/Time Bomb | Base |
| CWE-558 | Use of getlogin() in Multithreaded Application | Variant |
| CWE-655 | Insufficient Psychological Acceptability | Class |
| CWE-783 | Operator Precedence Logic Error | Base |

### Related CWEs

| CWE ID | Name |
|--------|------|
| CWE-779 | Logging of Excessive Data |
| CWE-1298 | Hardware Logic Contains Race Conditions |
| CWE-1313 | Hardware Allows Activation of Test or Debug Logic at Runtime |
| CWE-1323 | Improper Management of Sensitive Trace Data |
| CWE-143 | Improper Neutralization of Record Delimiters |
| CWE-532 | Insertion of Sensitive Information into Log File |
| CWE-533 | DEPRECATED: Information Exposure Through Server Log Files |
| CWE-534 | DEPRECATED: Information Exposure Through Debug Log Files |
| CWE-542 | DEPRECATED: Information Exposure Through Cleanup Log Files |

### CAPEC Attack Patterns

| CAPEC ID | Name | Severity | Attack Techniques |
|----------|------|----------|-------------------|
| CAPEC-189 | Black Box Reverse Engineering | Low | - |
| CAPEC-233 | Privilege Escalation | - | T1548 - Abuse Elevation Control Mechanism |
| CAPEC-26 | Leveraging Race Conditions | High | - |
| CAPEC-268 | Audit Log Manipulation | - | T1070, T1562.002, T1562.003 |
| CAPEC-624 | Hardware Fault Injection | High | - |
| CAPEC-625 | Mobile Device Fault Injection | - | - |
| CAPEC-663 | Exploitation of Transient Instruction Execution | Very High | - |
| CAPEC-676 | NoSQL Injection | High | - |
| CAPEC-74 | Manipulating State | High | - |

## Information Disclosure

**Description Keywords:** disclosure, exposure, leak, sensitive, privacy

### Primary CWEs

| CWE ID | Name | Abstraction |
|--------|------|-------------|
| CWE-200 | Exposure of Sensitive Information to an Unauthorized Actor | Class |
| CWE-209 | Generation of Error Message Containing Sensitive Information | Base |
| CWE-203 | Observable Discrepancy | Base |
| CWE-497 | Exposure of Sensitive System Information to an Unauthorized Control Sphere | Base |
| CWE-213 | Exposure of Sensitive Information Due to Incompatible Policies | Base |
| CWE-215 | Insertion of Sensitive Information Into Debugging Code | Base |
| CWE-1258 | Exposure of Sensitive System Information Due to Uncleared Debug Information | Base |
| CWE-1295 | Debug Messages Revealing Unnecessary Information | Base |
| CWE-201 | Insertion of Sensitive Information Into Sent Data | Base |
| CWE-311 | Missing Encryption of Sensitive Data | Class |
| CWE-359 | Exposure of Private Personal Information to an Unauthorized Actor | Base |
| CWE-532 | Insertion of Sensitive Information into Log File | Base |
| CWE-538 | Insertion of Sensitive Information into Externally-Accessible File or Directory | Base |
| CWE-1243 | Sensitive Non-Volatile Information Not Protected During Debug | Base |
| CWE-1273 | Device Unlock Credential Sharing | Base |

### Related CWEs

| CWE ID | Name |
|--------|------|
| CWE-170 | Improper Null Termination |
| CWE-257 | Storing Passwords in a Recoverable Format |
| CWE-732 | Incorrect Permission Assignment for Critical Resource |
| CWE-825 | Expired Pointer Dereference |
| CWE-863 | Incorrect Authorization |
| CWE-89 | Improper Neutralization of Special Elements used in an SQL Command ('SQL Injection') |
| CWE-1248 | Semiconductor Defects in Hardware Logic with Security-Sensitive Implications |
| CWE-1264 | Hardware Logic with Insecure De-Synchronization between Control and Data Channels |
| CWE-1268 | Policy Privileges are not Assigned Consistently Between Control and Data Agents |
| CWE-256 | Plaintext Storage of a Password |

### CAPEC Attack Patterns

| CAPEC ID | Name | Severity | Attack Techniques |
|----------|------|----------|-------------------|
| CAPEC-116 | Excavation | Medium | - |
| CAPEC-12 | Choosing Message Identifier | High | - |
| CAPEC-121 | Exploit Non-Production Interfaces | High | - |
| CAPEC-150 | Collect Data from Common Resource Locations | Medium | T1003, T1119, T1213 |
| CAPEC-157 | Sniffing Attacks | Medium | - |
| CAPEC-169 | Footprinting | Very Low | T1217, T1592, T1595 |
| CAPEC-189 | Black Box Reverse Engineering | Low | - |
| CAPEC-217 | Exploiting Incorrectly Configured SSL/TLS | - | - |
| CAPEC-22 | Exploiting Trust in Client | High | - |
| CAPEC-224 | Fingerprinting | Very Low | - |

## Denial of Service

**Description Keywords:** denial, dos, resource, exhaust, allocat

### Primary CWEs

| CWE ID | Name | Abstraction |
|--------|------|-------------|
| CWE-770 | Allocation of Resources Without Limits or Throttling | Base |
| CWE-400 | Uncontrolled Resource Consumption | Class |
| CWE-405 | Asymmetric Resource Consumption (Amplification) | Class |
| CWE-771 | Missing Reference to Active Allocated Resource | Base |
| CWE-920 | Improper Restriction of Power Consumption | Base |
| CWE-1325 | Improperly Controlled Sequential Memory Allocation | Base |
| CWE-1246 | Improper Write Handling in Limited-write Non-Volatile Memories | Base |
| CWE-789 | Memory Allocation with Excessive Size Value | Variant |
| CWE-1235 | Incorrect Use of Autoboxing and Unboxing for Performance Critical Operations | Base |
| CWE-362 | Concurrent Execution using Shared Resource with Improper Synchronization ('Race Condition') | Class |
| CWE-406 | Insufficient Control of Network Message Volume (Network Amplification) | Class |
| CWE-779 | Logging of Excessive Data | Base |
| CWE-908 | Use of Uninitialized Resource | Base |
| CWE-911 | Improper Update of Reference Count | Base |
| CWE-1341 | Multiple Releases of Same Resource or Handle | Base |

### Related CWEs

| CWE ID | Name |
|--------|------|
| CWE-226 | Sensitive Information in Resource Not Removed Before Reuse |
| CWE-122 | Heap-based Buffer Overflow |
| CWE-244 | Improper Clearing of Heap Memory Before Release ('Heap Inspection') |
| CWE-316 | Cleartext Storage of Sensitive Information in Memory |
| CWE-416 | Use After Free |
| CWE-646 | Reliance on File Name or Extension of Externally-Supplied File |
| CWE-121 | Stack-based Buffer Overflow |
| CWE-126 | Buffer Over-read |
| CWE-1274 | Improper Access Control for Volatile Memory Containing Boot Code |
| CWE-1282 | Assumed-Immutable Data is Stored in Writable Memory |

### CAPEC Attack Patterns

| CAPEC ID | Name | Severity | Attack Techniques |
|----------|------|----------|-------------------|
| CAPEC-100 | Overflow Buffers | Very High | - |
| CAPEC-123 | Buffer Manipulation | Very High | - |
| CAPEC-125 | Flooding | Medium | T1498.001, T1499 |
| CAPEC-130 | Excessive Allocation | Medium | T1499.003 |
| CAPEC-131 | Resource Leak Exposure | Medium | T1499 |
| CAPEC-212 | Functionality Misuse | Medium | - |
| CAPEC-227 | Sustained Client Engagement | - | T1499 |
| CAPEC-230 | Serialized Data with Nested Payloads | High | - |
| CAPEC-231 | Oversized Serialized Data Payloads | High | - |
| CAPEC-26 | Leveraging Race Conditions | High | - |

## Elevation of Privilege

**Description Keywords:** privilege, authorization, permission, access control, escalat

### Primary CWEs

| CWE ID | Name | Abstraction |
|--------|------|-------------|
| CWE-269 | Improper Privilege Management | Class |
| CWE-271 | Privilege Dropping / Lowering Errors | Class |
| CWE-267 | Privilege Defined With Unsafe Actions | Base |
| CWE-250 | Execution with Unnecessary Privileges | Base |
| CWE-266 | Incorrect Privilege Assignment | Base |
| CWE-268 | Privilege Chaining | Base |
| CWE-270 | Privilege Context Switching Error | Base |
| CWE-639 | Authorization Bypass Through User-Controlled Key | Base |
| CWE-648 | Incorrect Use of Privileged APIs | Base |
| CWE-274 | Improper Handling of Insufficient Privileges | Base |
| CWE-566 | Authorization Bypass Through User-Controlled SQL Primary Key | Variant |
| CWE-273 | Improper Check for Dropped Privileges | Base |
| CWE-689 | Permission Race Condition During Resource Copy | Compound |
| CWE-272 | Least Privilege Violation | Base |
| CWE-280 | Improper Handling of Insufficient Permissions or Privileges | Base |

### Related CWEs

| CWE ID | Name |
|--------|------|
| CWE-367 | Time-of-check Time-of-use (TOCTOU) Race Condition |
| CWE-294 | Authentication Bypass by Capture-replay |
| CWE-1191 | On-Chip Debug and Test Interface With Improper Access Control |
| CWE-1257 | Improper Access Control Applied to Mirrored or Aliased Memory Regions |
| CWE-1392 | Use of Default Credentials |
| CWE-1393 | Use of Default Password |
| CWE-220 | Storage of File With Sensitive Data Under FTP Root |
| CWE-259 | Use of Hard-coded Password |
| CWE-520 | .NET Misconfiguration: Use of Impersonation |
| CWE-529 | Exposure of Access Control List Files to an Unauthorized Control Sphere |

### CAPEC Attack Patterns

| CAPEC ID | Name | Severity | Attack Techniques |
|----------|------|----------|-------------------|
| CAPEC-1 | Accessing Functionality Not Properly Constrained by ACLs | High | T1574.010 |
| CAPEC-104 | Cross Zone Scripting | High | - |
| CAPEC-122 | Privilege Abuse | Medium | T1548 |
| CAPEC-17 | Using Malicious Files | Very High | T1574.005, T1574.010 |
| CAPEC-180 | Exploiting Incorrectly Configured Access Control Security Levels | Medium | T1574.010 |
| CAPEC-19 | Embedding Scripts within Scripts | High | T1027.009, T1546.004, T1546.016 |
| CAPEC-233 | Privilege Escalation | - | T1548 |
| CAPEC-234 | Hijacking a privileged process | Medium | - |
| CAPEC-26 | Leveraging Race Conditions | High | - |
| CAPEC-30 | Hijacking a Privileged Thread of Execution | Very High | T1055.003 |