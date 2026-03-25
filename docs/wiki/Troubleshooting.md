# Troubleshooting

## Browser returns to localhost and nothing happens

This usually means another application is already using the localhost OAuth callback port.

Common conflicts:

- VS Code
- another local OAuth listener
- another CAM or Codex login helper

## What to do

1. Close the conflicting application
2. Retry relay login
3. If needed, copy the callback URL and paste it into CAM Auth Manager manually
