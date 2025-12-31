# Secure Text

A serverless, encrypted messaging system that works entirely in your browser. Messages are encoded directly into URLs — no cloud, no database, no traces.

## How It Works

1. **You write a message** in the browser
2. **The message is compressed** and encoded into the URL hash (the part after `#`)
3. **You share just the hash** with your contact via any channel
4. **They decode it locally** using their own instance of the app

The message never touches a server — it lives entirely in the URL.

## Quick Start: Two-Way Secure Communication

### Step 1: Both Parties Get the App

Share the app files with your contact. You both need the same files:
- `index.html` (main editor)
- `md.html` (markdown editor)
- `qr.html` (QR code generator)

### Step 2: Run Locally

Each person runs a local server:

```bash
cd secure-text
python3 -m http.server 8000
```

Then open `http://localhost:8000` in your browser.

> **Alternative:** Just double-click `index.html` to open it directly (no server needed for basic usage).

### Step 3: Exchange Messages

1. **Write your message** in the editor
2. **Copy the hash** from your URL bar (everything after `#`):
   ```
   http://localhost:8000/#PckxCoRADAXQPqf4YLHVlB5C...
                         ↑ Copy this part only ↑
   ```
3. **Send the hash** to your contact via Signal, email, SMS, etc.
4. **They paste it** after their local URL:
   ```
   http://localhost:8000/#PckxCoRADAXQPqf4YLHVlB5C...
   ```
5. **Message decoded!** They see your message instantly.

### Step 4: Reply

They do the same in reverse — write a reply, copy the hash, send it back.

## Why This Is Secure

- **No server stores your data** — the message IS the URL
- **The hash never leaves your browser** — URL fragments (after `#`) are not sent to servers
- **End-to-end by design** — only people with the hash can read the message
- **No accounts, no logs, no metadata**

## Tools

| URL | Purpose |
|-----|---------|
| `/` or `/index.html` | Plain text editor |
| `/md.html` | Markdown editor with syntax highlighting |
| `/qr.html` | Generate QR code for sharing |

## Tips

- Start your message with `# Title` to set a custom page title
- Use `Cmd/Ctrl + S` to download the message as a standalone HTML file
- Add `/qr.html` to generate a scannable QR code of your message
- Use `/md.html` for formatted messages with **bold**, *italic*, `code`, etc.

## Hosting Options

If you want a shared URL instead of exchanging hashes:

1. **GitHub Pages** (free) — Host the app publicly, share full URLs
2. **Your own server** — Any static file host works
3. **Local only** — Both parties run locally, share just the hashes

---

*No cloud. No database. No traces. Just you and the URL.*
