# Security Policy

## Overview

NoRelay is a **serverless, peer-to-peer, end-to-end encrypted messaging system**.  
Security, privacy, and transparency are core design goals of this project.

NoRelay does **not** use central servers, relays, or third-party infrastructure.  
All communication occurs **directly between peers** and is protected using modern cryptographic protocols.

This document describes how to responsibly report security issues and what guarantees NoRelay provides.

---

## Supported Versions

Security updates apply to the **latest released version** of NoRelay.

| Version | Supported |
|--------|-----------|
| Latest | ✅ Yes |
| Older releases | ❌ No |

Users are strongly encouraged to upgrade to the latest version.

---

## Threat Model (High-Level)

NoRelay is designed to protect against:

- Passive network surveillance
- Message interception and tampering
- Man-in-the-middle (MITM) attacks
- Replay attacks
- Compromise of past messages (forward secrecy)

NoRelay does **not** attempt to hide:

- IP addresses from peers
- The fact that two peers are communicating
- Traffic timing or volume

---

## Cryptographic Design Summary

NoRelay uses the following cryptographic primitives:

- **Identity Keys**  
  - RSA (4096-bit) long-term identity keys

- **Key Agreement**  
  - X25519 (Elliptic Curve Diffie-Hellman)

- **Session Security**  
  - Double Ratchet algorithm (forward secrecy & post-compromise security)

- **Message Encryption**  
  - AEAD (e.g. ChaCha20-Poly1305 or AES-GCM)

- **Integrity & Authentication**  
  - Cryptographic signatures and authenticated encryption

All cryptographic operations are implemented using well-reviewed libraries.  
Custom cryptographic primitives are **not** used.

---

## Trust & Identity Verification

- Users authenticate peers via **cryptographic fingerprints**
- Fingerprints must be manually verified on first connection
- Accepted fingerprints are stored locally and reused for future sessions

NoRelay does **not** rely on usernames, phone numbers, emails, or central identity servers.

---

## Data Storage & Persistence

NoRelay minimizes stored data:

- Messages are stored only in **small, local, in-memory queues**
- Default message buffer length is limited and configurable
- No message history is retained beyond the configured buffer
- Keys and session data are stored **only on the local machine**

The `--reset` command permanently deletes all locally stored keys, peers, and sessions.

---

## Responsible Disclosure

If you discover a security vulnerability, **do not open a public issue**.

Please report security issues **privately**.

### How to Report

Send an email to:
security@norelay.chat


Include:
- A clear description of the issue
- Steps to reproduce (if applicable)
- Potential impact
- Any proof-of-concept code (optional)

We will acknowledge receipt within **72 hours**.

---

## Vulnerability Handling Process

1. Report is received and acknowledged
2. Issue is investigated privately
3. Fix is developed and tested
4. A new version is released
5. Security advisory is published (if applicable)

We aim to resolve critical vulnerabilities as quickly as possible.

---

## Security Audits

NoRelay welcomes:

- Independent code review
- Cryptographic analysis
- Formal audits

If you are interested in auditing NoRelay, please contact the security team.

---

## Disclaimer

NoRelay is provided **"as is"**, without warranty of any kind.  
While best practices are followed, no software can be guaranteed to be completely secure.

Users are responsible for:
- Verifying peer fingerprints
- Keeping their systems updated
- Protecting their private keys

---

## Contact

For all security-related matters:
security@norelay.chat

---

*Last updated: 2025*

