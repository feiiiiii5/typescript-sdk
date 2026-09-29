---
'@modelcontextprotocol/client': patch
'@modelcontextprotocol/server': patch
---

`UriTemplate` now honors the explode modifier for the label (`.`) and path (`/`) operators. A non-exploded list expands comma-joined (`{/list}` with `['a', 'b']` → `/a,b`) like every other operator, an exploded list expands with the operator's separator, and `match()` understands both forms — so a URI produced by `expand()` routes back to the handler instead of coming back `null` (`Resource not found` from `resources/read`).
