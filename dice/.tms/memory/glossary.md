# Glossary

Domain terms used in this project. The plugin reads this when it
encounters unfamiliar terms in SOT or when generating cases.

Add entries as you go. Edit freely.

> Empty starter — no existing cases to scan during /setup. Seed terms
> after the first spec/feature pass.

## Format

```yaml
- term: <canonical term>
  aliases: [<other spellings or synonyms>]
  in_cases: <how this term should appear in case text>
  notes: <optional context>
```

## Entries

```yaml
- term: Tavern Dice
  aliases: [dice]
  in_cases: "Tavern Dice"
  notes: "The product — a dice game with user accounts, a chip economy, and a leaderboard."

- term: chips
  aliases: [фишки, баланс]
  in_cases: "фишки"
  notes: "In-game currency balance on the user. DB CHECK (chips >= 0) — cannot go negative. New users get STARTING_CHIPS (default 1000)."

- term: STARTING_CHIPS
  aliases: [стартовые фишки]
  in_cases: "стартовые фишки (STARTING_CHIPS)"
  notes: "Env-configurable starting balance granted at registration; default 1000."

- term: JWT
  aliases: [token, токен, Bearer token]
  in_cases: "JWT / токен"
  notes: "HS256, signed with JWT_SECRET. Claims: sub=userId, iat, exp. TTL = 7 days (constant tokenTTL, not env). Sent as 'Authorization: Bearer <token>'."

- term: user_stats
  aliases: []
  in_cases: "user_stats"
  notes: "Per-user stats row (wins, games_played, net_chips), created in the same transaction as the user at registration, all zero."

- term: tavern_dice_session
  aliases: [session key]
  in_cases: "ключ localStorage tavern_dice_session"
  notes: "localStorage key holding the client session { token, username }. Survives reload."

- term: anti-enumeration
  aliases: [user enumeration protection]
  in_cases: "защита от перечисления пользователей"
  notes: "Login returns identical 401 INVALID_CREDENTIALS for unknown-user and wrong-password (response + timing) so usernames can't be probed."

- term: alg-confusion
  aliases: [algorithm confusion]
  in_cases: "alg-confusion"
  notes: "JWT attack where the verifier is tricked via the token's alg header (e.g. alg:none, RS256). Closed here: algorithm hard-pinned to HS256."
```
