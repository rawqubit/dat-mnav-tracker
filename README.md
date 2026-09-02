# DAT mNAV Tracker

Live multiple-of-NAV dashboard for the eight Digital Asset Treasuries from the CRYPTO DATS watchlist:

`AVAT` · `MSTR` · `BMNR` · `PURR` · `USDE` · `CYPH` · `FWDI` · `CNTN`

## Open the app

1. Clone or download this repo.
2. Open `index.html` in a browser (double-click is enough).
3. Or enable GitHub Pages on this repo (Settings → Pages → Deploy from `main` / root).

Live URL after Pages is on:
`https://rawqubit.github.io/dat-mnav-tracker/`

Raw preview:
https://htmlpreview.github.io/?https://github.com/rawqubit/dat-mnav-tracker/blob/main/index.html

## What it computes

| Lens | Formula |
|---|---|
| Basic mNAV | Market cap / crypto NAV |
| EV mNAV | (Market cap + debt − cash) / crypto NAV |
| FD mNAV | Diluted shares × price / crypto NAV |
| Pref EV (MSTR) | (Market cap + debt + preferred − cash) / crypto NAV |

Crypto NAV = last disclosed tokens × live spot.

## Data sources

- Token spots: [CoinGecko](https://api.coingecko.com/api/v3/simple/price) (auto-refresh 60s)
- Stock quotes: Yahoo Finance (direct, then CORS proxies)
- Holdings: `holdings.json` — last 8-K / 10-Q / IR print baked in

If a quote API is blocked, the app falls back to the Sep 1, 2026 close and marks the row `STALE`.

## Update holdings after a new 8-K

Edit `holdings.json` (token count, share count, cash, debt) and refresh the page.
The dashboard also lets you override any field in the browser; overrides persist in `localStorage`.

## Not financial advice

Trackers disagree on share counts and capital-structure lenses. This app shows all three so you do not mix a 0.74x common print with a 1.07x preferred-inclusive print.
