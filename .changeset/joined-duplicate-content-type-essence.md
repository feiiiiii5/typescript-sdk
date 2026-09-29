---
'@modelcontextprotocol/client': patch
'@modelcontextprotocol/server': patch
---

`mediaTypeEssence` now yields no essence for an unparseable `Content-Type` that carries a comma anywhere in the value, not only in its parameter section. `Headers.get()` joins repeated headers with `, `, so `Content-Type: application/json, application/json` (two copies, or a proxy appending one) put the comma inside the media-type segment itself, where the previous check looked past it and returned `'application/json, application/json'` as the essence. No call site changed behavior — every one compares the essence against a known media type, and a bogus string failed those comparisons exactly as `undefined` did — but the returned value now matches the function's documented contract.
