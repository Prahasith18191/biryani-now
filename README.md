# 🍚 Biryani Now

Settle the group argument once and for all: **where do we go for the best Hyderabadi biryani RIGHT NOW?**

A single-file, zero-build micro web-app that ranks real Hyderabadi biryani spots by live votes, filters them by how far you're willing to travel, and roasts your empty states in proper Hyderabadi street slang.

**Live demo:** deployed on Google Cloud Run (see repo description / deployment output).

---

## The three mechanics

1. **Live voting + distance filter.** Tap a spot to vote; the leaderboard instantly re-ranks by vote count with a smooth transform transition and a crown on #1. A distance slider ("within X km") filters out anything farther than the chosen radius — the board and the "Tonight's winner" hero update live. Votes persist in `localStorage`.

2. **Secret local knowledge.** A hand-curated, hardcoded list of ten **real** Hyderabadi biryani spots (Shadab, Café Bahar, Shah Ghouse, Bawarchi, Pista House, Hotel Nayaab, Sarvi, Meridian, Alpha, Niagara) — each with its area, approx distance, and a one-line insider note you'd only get from a local. You can also add your own secret spot (name + area + km), persisted locally.

3. **Slang rewriter.** A small `slangify(kind)` function rewrites boring error/empty states into playful Hyderabadi street slang — no-spots-in-range, ties, add-confirmations, and rotating traffic/parking warnings on the winner card (e.g. *"Parking milega nai, auto me jao 🛺"*).

---

## Run it

Just open `index.html` in a browser. No build step, no dependencies, no backend. State lives in `localStorage`.

## Deploy

Containerised with nginx and shipped to Google Cloud Run:

```bash
gcloud run deploy biryani-now --source . --region=us-central1 --allow-unauthenticated --port=8080
```

`nginx.conf` is kept as a separate file (not inlined in the Dockerfile) so the `$uri` variable survives.

---

Built with **Google Antigravity** · Vibe Coding Lounge
