# Parasite Block Monitor

A live monitor for blocks mined by the [Parasite pool](https://parasite.space). One HTML file, nothing else.

**Use it here:** open the page and leave the tab open. When Parasite finds a block, the page takes over the screen with the block's real shape — every rectangle is an actual transaction, sized by weight, colored by fee rate — plus a browser notification if you enable alerts.

**Or run it locally:** click "Download this page" (or grab `index.html` from this repo) and double-click the file. It works identically offline-installed — no server, no dependencies.

## How it works

Your browser connects directly to mempool.space's public API:

- `wss://mempool.space/api/v1/ws` — live block feed (`{"action":"want","data":["blocks"]}`), matched on `extras.pool` = Parasite
- `GET /api/v1/mining/pool/parasite/blocks` — history backfill
- `GET /api/v1/block/<hash>/summary` — the real per-transaction block shape

That is the complete list of network calls. No analytics, no accounts, no cookies, no server behind this page. Found blocks are remembered in your browser's localStorage.

The whole thing is readable in this one file — fonts and the block animation are embedded so it stays self-contained.

## License

Public domain (Unlicense). Do whatever you want with it.
