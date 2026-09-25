# CipherLab - Web-Based Text Encryption Tool

## Overview
CipherLab is a single-page web application that encrypts user-supplied text entirely client-side. Users enter plaintext, select an algorithm from a dropdown, and click **Encrypt** to view the ciphertext. All processing runs in the browser via the native **Web Crypto API** - no data leaves the device.

## Encryption Techniques
- **Caesar Cipher** — Classical substitution: `E(x) = (x + k) mod 26`. Case-preserving, reversible with shift `−k`.
- **Base64** — Reversible binary-to-text encoding (not encryption); included for completeness.
- **AES-256-GCM** — Password-based; PBKDF2-HMAC-SHA256 (150,000 iterations) derives the key from a random 16-byte salt. A 12-byte IV ensures uniqueness. GCM supplies confidentiality *and* integrity. Output: `AESGCM:salt:iv:data`.
- **RSA-OAEP (2048-bit)** — Hybrid scheme: a random AES-GCM key encrypts the message, then RSA wraps that key. Output: `RSAOAEP:wrappedKey:iv:data`.
- **SHA-256** — One-way cryptographic hash producing a 64-character hex digest.

## Features
Validation blocks empty input and missing method selection. **Decrypt** reverses reversible methods; **Copy** uses the Clipboard API with a fallback; **Clear** resets the form. RSA keys persist only for the session.

## Tech Stack
HTML5, CSS3, vanilla JavaScript (ES6+), Web Crypto API. No external dependencies.
