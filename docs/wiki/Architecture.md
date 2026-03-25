# Architecture

The extension is intentionally small.

## Flow

1. User starts relay login from popup
2. Manager returns/open login flow
3. Browser completes OpenAI/Codex login
4. Localhost callback appears in browser
5. Extension intercepts callback URL
6. Extension relays callback data back to CAM Auth Manager
7. Manager finalizes auth handling

## Scope

The extension does not manage account storage itself.
That remains the responsibility of CAM Auth Manager.
