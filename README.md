# seal-key

A single offline page for sealing an API key to send to a Discord bot

## What it's for

If you use the bot and it says you need to register a key, this page is where you
do the first step. You paste your own API key here, it gets **encrypted in your
browser** to the bot's public key, and you get a sealed blob to hand the bot via
`/setkey`. Your raw key never leaves your browser and never travels over Discord —
only the sealed version does.

## How to use it

1. Open the page: **https://zourage.github.io/seal-key/**
2. Paste your API key and your Discord user ID
   (Discord → Settings → Advanced → Developer Mode on, then right-click your name → Copy User ID)
3. Click **Seal my key**, copy the sealed blob
4. DM the bot `/setkey` and paste the blob

## Why you can trust it

- The page makes **no network requests** — no fetch, no form submission, nothing
  leaves your browser. It ships a Content-Security-Policy that makes your browser
  enforce that.
- The sealing happens entirely client-side with the Web Crypto API.
- The only key in this file is the bot's **public** key (safe to share, by design).
  It cannot decrypt anything — it can only encrypt *to* the bot.
- The page is a single static file. You can read the whole thing.
