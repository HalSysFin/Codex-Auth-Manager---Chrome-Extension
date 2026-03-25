# CAM - Chrome Relay Extension First-Time Setup

This guide gets the Chrome extension working for the first time with CAM Auth Manager.

## 1. Load the extension

1. Open `chrome://extensions`
2. Enable **Developer mode**
3. Click **Load unpacked**
4. Select this repository folder

## 2. Configure the extension

Open the extension popup or Options page and set:

- **Auth Manager Base URL**
  - example: `https://your-domain`
  - local example: `http://localhost:8080`
- **Internal API Bearer Token** if required by your CAM Auth Manager deployment

## 3. Check the manager is reachable

Make sure CAM Auth Manager is up before starting relay login.

Typical local URLs:

- backend: `http://localhost:8080`
- bundled frontend: usually served by the backend image
- dev frontend, if used: `http://localhost:5173`

## 4. Avoid callback conflicts

Before testing login, close apps that may already be using localhost callback ports such as `1445` or `1455`.

Especially watch for:

- VS Code login windows
- other OAuth tools
- anything already listening on localhost auth callback ports

## 5. Test relay login

1. Open the extension popup
2. Click **Start Relay Login**
3. Finish the browser login flow
4. Confirm the callback is relayed to CAM Auth Manager

## 6. If it hangs

If the browser returns to localhost and nothing happens:

1. copy the full callback URL
2. open CAM Auth Manager
3. click **Add Account**
4. paste the callback URL into the modal
5. submit it manually

## 7. Verify success

After a successful relay, confirm in CAM Auth Manager that:

- the login completed
- the account appears in the manager
- the auth is persisted correctly
