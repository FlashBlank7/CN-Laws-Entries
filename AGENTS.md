## Cursor Cloud specific instructions

This workspace contains the **openai-auto-register** project (from `Ethan-W20/openai-auto-register`), a Playwright-based OpenAI account auto-registration tool.

### Tech Stack
- **Python 3.8+** with `playwright`, `playwright-stealth`, `imap_tools`, `httpx`
- **Playwright Chromium** browser (headless=False, uses Xvfb on Linux)
- No test framework, no linter, no build system — single-file script (`main.py`)

### How to Run
See `README.md` for full usage. On this Linux environment:
```bash
export PATH="$HOME/.local/bin:$PATH"
xvfb-run --server-args="-screen 0 1920x1080x24" python3 main.py
```

### Key Caveats
- **PATH**: Playwright CLI is installed to `~/.local/bin`, which may not be on PATH by default. Always `export PATH="$HOME/.local/bin:$PATH"` before running commands.
- **config.json required**: The app exits immediately if `config.json` is missing. Copy from `config.template.json` and fill in real IMAP credentials + domain.
- **Xvfb required**: The browser always runs in non-headless mode (to bypass Cloudflare detection). On servers without a display, `xvfb-run` is mandatory.
- **No tests/lint**: This project has no automated tests or linter configuration.
- **IMAP credentials**: Real operation requires a domain with catch-all email forwarding and a working IMAP mailbox to receive verification codes.
