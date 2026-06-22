# Data sources

The app reads local usage sources in read-only mode.

## Codex

Default path:

```text
%USERPROFILE%\.codex\sessions
```

Parser behavior:

- Walks `*.jsonl` files recursively.
- Reads one JSON object per line.
- Ignores malformed JSON lines and reports a warning count.
- Uses the latest complete token snapshot per session file.
- Extracts metadata such as session id, timestamp, model, project path, and title when present.

Supported token paths:

```text
payload.total_token_usage
payload.last_token_usage
payload.info.total_token_usage
payload.info.last_token_usage
```

Real Codex token events may look like:

```text
type = "event_msg"
payload.type = "token_count"
payload.info.total_token_usage
payload.info.last_token_usage
```

If Codex tokens show as zero despite active usage, check that parser tests cover this shape.

## WorkBuddy

Default path:

```text
%USERPROFILE%\.workbuddy\workbuddy.db
```

Parser behavior:

- Opens SQLite with read-only flags.
- Reads `session_usage`.
- Left joins `sessions` on `sessions.id = session_usage.session_id`.
- Reads optional fields defensively because local schemas can differ.
- Sums numeric values in `credit_json` into `credit_total` when present.

WorkBuddy `used`, `size`, and `credit_total` are WorkBuddy usage fields. Do not label them as Codex tokens.

## Privacy rules

- Do not modify source files.
- Do not write back to `.codex` or `.workbuddy`.
- Do not copy prompts, responses, or tool output into docs or logs.
- When creating public docs, use `%USERPROFILE%` instead of personal absolute paths.
