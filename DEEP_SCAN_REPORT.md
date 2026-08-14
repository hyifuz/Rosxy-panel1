# Rosxy Panel Deep Scan / v2

## Checks
- HTML JavaScript syntax: PASS (all inline script blocks)
- Duplicate HTML IDs: PASS
- `location.reload()` loops: none found
- `eval(`: none found
- `new Function`: found only inside bundled runtime/polyfill; not application code
- Owner manifest: PASS
- HTML SHA-256 manifest: PASS
- ZIP integrity: PASS

## Fixes
1. Integrity verification now gates page visibility until the external manifest and page hash both validate.
2. The verifier now detects modification of the HTML itself, not only removal of the watermark elements.
3. Missing/invalid integrity manifest prevents application startup.
4. Verification uses SHA-256 through Web Crypto and no executable code from the manifest.
5. Added explicit cache-bypass on integrity fetches.
6. Kept the owner marker as `@hyifu owner`.

## Limitation
Client-side integrity cannot be made unbypassable when an attacker controls both the HTML and its manifest. For strong tamper resistance, enforce the same hash/signature check at the server/CDN layer.
