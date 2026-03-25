# Codex Auth Manager - Chrome Relay Extension

This Chrome extension works with Codex Auth Manager to capture and relay localhost authentication callbacks during browser-based login flows. It helps move authentication from a local browser session into the central Auth Manager service for storage and later use.

## Features

- Start relay-backed login from the browser
- Capture localhost callback URLs such as `http://localhost:1455/auth/callback`
- Relay callback payloads back to CAM Auth Manager
- Reduce manual copy/paste during login
- Keep a manual fallback path when localhost callback conflicts exist

## Works With

This extension is designed to work with [Codex Auth Manager](https://github.com/HalSysFin/codex-auth-manager).
- It relays the authentication flow from a local machine to the Codex Auth Manager server, where credentials can be stored and managed centrally.

## Known Issues

- Authentication may fail if VS Code, or any other process, is already using port 1455 on the machine where the relay extension is installed.
- For the smoothest experience, close VS Code before starting the relay flow.

Expected backend endpoints:

- `POST /auth/login/start-relay`
- `POST /auth/relay-callback`
- `GET /auth/login/status`

## Install

### Load unpacked in Chrome

1. Open `chrome://extensions`
2. Enable **Developer mode**
3. Click **Load unpacked**
4. Select this repository folder

## Configure

Open the popup or Options page and set:

- **Auth Manager Base URL**
  - example: `https://your-domain`
  - local example: `http://localhost:8080`
- **Internal API Bearer Token** if your backend requires it

## Normal Flow

1. Open the extension popup: Set a shortcut with "ctrl + shift + L"
2. Click **Start Relay Login**
3. Complete the browser login flow
4. The extension captures the localhost callback URL
5. The extension relays it back to CAM Auth Manager
6. CAM Auth Manager continues the login flow on the server side

## Manual Fallback

If the browser lands on a localhost callback URL and nothing happens:

1. Copy the full callback URL
2. Open CAM Auth Manager
3. Click **Add Account**
4. Paste the callback URL into the modal
5. Submit it so the manager can finalize the login manually

## Localhost Callback Conflicts

If another app is already listening on callback ports such as `1455`, the relay may fail or hang.

Common causes:

- VS Code auth flows
- tools that bind localhost OAuth callback ports
- other browser-assisted login tools

Common symptoms:

- the login flow hangs
- the browser returns to localhost but nothing finalizes
- the callback appears in the browser but the manager does not update

Best practice:

- close tools that may be using localhost auth callback ports before starting relay login
- if there is a conflict, retry after stopping the conflicting app
- if needed, use the manual fallback flow in CAM Auth Manager

## Shortcuts

- Open popup: `Ctrl+Shift+Y` (`Command+Shift+Y` on macOS)
- Start relay login: `Ctrl+Shift+L` (`Command+Shift+L` on macOS)

## Security Notes

- this extension only relays callback data to the configured CAM Auth Manager backend
- if your backend is protected, use the correct bearer token
- do not point the extension at an untrusted server

## Documentation

- [First-Time Setup](./FIRST_TIME_SETUP.md)
- [Contributing](./CONTRIBUTING.md)
- [Security Policy](./SECURITY.md)
- [Wiki Pages](./docs/wiki/Home.md)

## Files

- `manifest.json`
- `background.js`
- `popup.html`
- `popup.js`
- `options.html`
- `options.js`

## License

Released under the MIT License. See [LICENSE.txt](./LICENSE.txt).

