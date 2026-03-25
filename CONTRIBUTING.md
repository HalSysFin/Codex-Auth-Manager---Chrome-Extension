# Contributing

Thanks for helping improve CAM - Chrome Relay Extension.

## Development Principles

- keep the extension small and focused on browser relay behavior
- keep compatibility with CAM Auth Manager login endpoints
- prefer clear fallback behavior over silent failure
- document localhost callback conflict cases carefully

## Local Testing

1. Open `chrome://extensions`
2. Enable **Developer mode**
3. Load the repository as an unpacked extension
4. Open the popup and verify:
   - settings save correctly
   - relay login opens a browser flow
   - callback relay works
   - manual fallback guidance is accurate

## Pull Requests

Please include:

- a short summary of the change
- testing notes
- any user-facing behavior changes
- screenshots if the popup or options UI changed
