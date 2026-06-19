# Tag taxonomy

Tags used in this project's cases. The plugin uses this to:
- Suggest correct tags to workers (preventing tag drift)
- Identify cases for `/update-feature` searches
- Surface coverage gaps

<!-- Format:
- tag: <tag>
  meaning: <what it indicates>
  applies_to: <kind of case>
  required_with: [<other tags that must accompany this one>]
-->

## Entries

# Baseline tags seeded by /setup. These four appear in almost every project,
# so the plugin pre-registers them — workers can use them on the first
# /new-feature without the Lead having to extend the taxonomy retroactively.
# Add project-specific tags below as you go.

- tag: smoke
  meaning: "Release-gate; runs on every build. Critical happy paths only."
  applies_to: "The minimum set that proves the feature is alive."
  required_with: []

- tag: regression
  meaning: "Included in the full regression cycle."
  applies_to: "Cases covering areas that have historically had bugs, or that guard against re-introductions."
  required_with: []

- tag: negative
  meaning: "Negative / reject scenario — the system correctly rejects invalid input or unauthorized action."
  applies_to: "All validation, error-handling, and access-denied cases."
  required_with: []

- tag: tbd
  meaning: "Case is blocked by an unresolved spec gap and is parked in `status: draft` until the question is answered."
  applies_to: "Any case where the worker hit a question only product/design can answer. Pair with an entry in `learned/patterns.md` describing the open question."
  required_with: []

# Project-specific tags for `dice` — extend as the taxonomy grows:

- tag: api
  meaning: "API-level (not UI) testing."
  applies_to: "Cases that interact with the API directly (contract, status codes, schema)."
  required_with: []

- tag: security
  meaning: "Security-relevant scenario (OWASP manual QA scope)."
  applies_to: "Auth, access control, input validation, sensitive-data cases."
  required_with: []

# Added during /new-feature confluence:9207811 (auth & registration):

- tag: auth
  meaning: "Authentication / authorization domain."
  applies_to: "Every case touching registration, login, JWT, or session."
  required_with: []

- tag: registration
  meaning: "Account-creation endpoint (POST /api/v1/register)."
  applies_to: "Registration validation, side-effects, duplicate/case-sensitivity."
  required_with: [auth]

- tag: login
  meaning: "Login endpoint (POST /api/v1/login)."
  applies_to: "Login success/failure, anti-enumeration, JWT issuance."
  required_with: [auth]

- tag: session
  meaning: "Client-side session, route guard, UI auth flows."
  applies_to: "Frontend localStorage/session-store/redirect behaviour."
  required_with: [auth, web]

- tag: jwt
  meaning: "JWT structure / claims / middleware token validation."
  applies_to: "Token decode, TTL, signature, alg-pinning, sub checks."
  required_with: [auth]

- tag: web
  meaning: "Frontend / browser UI behaviour (vs api)."
  applies_to: "Cases executed against the UI rather than the HTTP contract."
  required_with: []

- tag: needs-tooling
  meaning: "Cannot be run with plain HTTP/UI alone; needs a helper (JWT signer with JWT_SECRET / wrong secret / alg:none / past exp; timing samples; DB/admin read)."
  applies_to: "Crafted-token, timing-parity, and non-observable side-effect cases. State the prerequisite in the case ## Notes."
  required_with: []
