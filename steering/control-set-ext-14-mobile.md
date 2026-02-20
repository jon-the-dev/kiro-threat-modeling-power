<!-- VERSION_FIXME -->

# Control Set 15: Mobile Security (MOBILE)

**Domain**: MOBILE - Mobile Security
**Version**: 1.0
**Last Updated**: 2025-12-30

---

## Overview

Mobile security control set, applicable to iOS/Android native and cross-platform applications. Loaded on demand when the following trigger conditions are detected:

- iOS projects (*.xcodeproj, Podfile)
- Android projects (build.gradle, AndroidManifest.xml)
- React Native (react-native.config.js)
- Flutter (pubspec.yaml)

---

## Core Controls

### MOBILE-01: Secure Local Storage

**Control Requirement**: Local storage must be encrypted and protected

- Use platform secure storage (Keychain/Keystore)
- Encrypt sensitive data at rest
- Prohibit plaintext credential storage
- Clean up data on application uninstall

### MOBILE-02: Transport Security

**Control Requirement**: Network transport must be secure

- Enforce HTTPS communication
- Certificate Pinning
- Prohibit insecure TLS configurations
- Detect proxy/man-in-the-middle attacks

### MOBILE-03: Code Protection

**Control Requirement**: Application code must be protected

- Code obfuscation (ProGuard/R8/SwiftShield)
- Prevent decompilation and debugging
- Resource file encryption
- Implement sensitive logic on the server side

### MOBILE-04: Runtime Protection

**Control Requirement**: Runtime environment must be secure

- Detect jailbroken/rooted devices
- Prevent dynamic injection
- Integrity verification
- Debug detection and blocking

### MOBILE-05: Authentication Security

**Control Requirement**: Mobile authentication must be secure

- Biometric integration (Face ID/Touch ID)
- Secure session management
- Device binding and registration
- Offline authentication strategy

### MOBILE-06: Data Leakage Prevention

**Control Requirement**: Prevent data leakage

- Prohibit sensitive data on clipboard
- Screenshot protection
- Log sanitization
- Third-party SDK auditing

---

## L4 References

Detailed practice guides are available in the `references/` directory:

- reference-set-15-mobile-security.md
- reference-set-15-certificate-pinning.md

---

## STRIDE Mapping

| STRIDE | Applicable Controls |
|--------|---------------------|
| S | MOBILE-04, MOBILE-05 |
| T | MOBILE-03, MOBILE-04 |
| R | MOBILE-05 |
| I | MOBILE-01, MOBILE-02, MOBILE-06 |
| D | MOBILE-04 |
| E | MOBILE-04, MOBILE-05 |
