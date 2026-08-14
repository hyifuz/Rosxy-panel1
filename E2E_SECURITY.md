# Rosxy Panel E2E Protection

Added a browser-side cryptographic envelope for sensitive panel state.

- AES-256-GCM confidentiality
- PBKDF2-SHA-256 key derivation
- 310,000 PBKDF2 iterations
- Random 128-bit salt per envelope
- Random 96-bit AES-GCM IV per envelope
- Independent HMAC-SHA-256 integrity/authenticity check
- No plaintext secret is placed in the E2E status indicator
- Secret material is not persisted by the E2E module

JavaScript API:
- `RosxyE2E.seal(value, passphrase)`
- `RosxyE2E.open(packet, passphrase)`
- `RosxyE2E.generateSecret()`

Important: browser-side E2E protects data handled by the browser, but cannot protect a secret that is deliberately sent to a server. Production authentication and authorization must still be enforced server-side over HTTPS, with secure cookies/session rotation and server-side access control.
