# Bigbull 1.1 — Indian equity research

Created by **Harsh Prashant Gattani**.

Download the signed APK from [GitHub Releases](https://github.com/finalstop/Bigbull/releases). The complete buildable project is distributed as `Bigbull-1.1-source.zip`: extract it, enter the `Bigbull` folder, then follow the build steps below.

Native Kotlin / Jetpack Compose, Android **9+**, target/compile SDK 35. Version 1.1.0, code 12. Non-debuggable, R8-optimized release signed with a private certificate. No ad SDK, paid API key, subscription or feature locks.

## New in 1.1

- Animated technical barometer: **Strong buy / Can buy / Neutral / Can sell / Strong sell**, a transparent 0–100 score, seven disclosed trend/momentum votes, and bullish/neutral/bearish counts. Missing indicators are excluded; four valid votes are required. Ratings use the selected completed daily, weekly or monthly history with its actual date.
- Cleaner reader: ET image variants share one asset identity, promotional blocks and audio prompts are excluded, article-body content is preferred, and genuine distinct article images remain.
- Indian Express replaced by **NDTV.com / NDTV Profit**, using its published business RSS feed. ET, Mint and India Today remain. No article text or images are bundled.
- A private per-stock **Research journal**: thesis, invalidation conditions, evidence links, next review date, persistent local save and text export. Review dates appear inside the journal; no notification scheduling. This was selected from qualitative investor discussions about scattered research and revisiting a concise thesis, not claimed as a statistically most-requested or unique feature.
  - https://www.reddit.com/r/ValueInvesting/comments/1getr71/
  - https://www.reddit.com/r/investing/comments/1sw2tmb/

## Retained from 1.0

- Rounded glass navigation without rectangular press/focus shading. BB monogram, creator credit, dark/light themes and animated Fear & Greed gauge remain.
- Official NIFTY 500, NIFTY 50 and ten sector universes; all NSE EQ; supported BSE equities; BSE-only companies; watchlists. Browse the companies or run investor playbooks. No 20-stock limit. BSE-only uses ISIN exclusion against the NSE cash-market directory in Upstox's public instrument files, not ticker-name matching. This covers supported securities, not all possible exchange listings. Bonds, funds, derivatives and invalid identifiers are excluded.
- Minervini strictly requires all eight Trend Template rules. SMA200 is compared with 21 completed sessions ago; a temporary dip does not fail the month-long slope test. Price must be at least 30% above its 52-week low and within 25% of the high. Bigbull RS is a disclosed 12-month price-return percentile versus eligible NIFTY 500 members at a common completed session, with midpoint ties. This is **not IBD's proprietary rating**. At least 300 eligible members and at most 5% fetch failures; full coverage counts are shown. Missing inputs disqualify. No partial seven-rule stock is a match.
- Optional SEPA financial filters: quarterly EPS YoY >=25%, revenue YoY >=20%, expanding net margin and annual ROE >=17%. Does not infer earnings surprises, institutional sponsorship, VCP or trade execution. Buffett, Graham and Lynch approaches retain their transparent partial interpretations and formulas.
- Large scans use three concurrent requests, cancellation, bounded in-memory history/report retention and per-stock errors. Keep the app open during scans. Constituent downloads, synchronized prices/reports and calendars can be cached when offline retention is enabled. BSE directories currently have a six-hour in-memory cache. Source history may be sparse, especially on BSE; unavailable inputs never become passing values.
- NSE upcoming results meetings and declared cash dividends. Client-side date filtering, cancellation and explicit rescheduling handling. Ex-dividend dates and record dates remain separate. Meeting dates do not guarantee result-publication timing.
- Annual Reports tab and overview shortcut. NSE filing metadata supplies original dated PDF links. BSE uses public Screener document indexing to original exchange PDFs; that index or the exchange may block requests, and the UI reports unavailable access. Native in-app PDF reader, previous/next, page jump, zoom, visible loading/retry/error and original source link. Up to 64 MB, temporary file deleted when closed; ZIP attachments use the original source link. No paywall bypass, PDF text generation or fabricated reports.
- ET hero/body image resize variants are deduplicated across image hosts. Distinct charts and photos remain. News feeds: Economic Times, Mint, India Today and NDTV.com / NDTV Profit. Business Standard removed. Sponsored/brand-post URLs excluded. Native reader runs no article JavaScript, iframes or ad widgets. Publisher subscription restrictions remain respected.
- Company logos on stock/mover, calendar and screen-result rows. On-demand Groww image CDN with memory cache and initials fallback; no affiliation implied.

## Existing working features

Same-day public quotes and five-minute charts with timestamps; completed daily/weekly/monthly history; interactive charts and technical indicators; visual financial statements, peer ratios and annual P/E/P/B; automatically populated intrinsic-value scenarios with visible assumptions; published six-group Tickertape MMI; multiple watchlists; portfolio ledger, fees/P&L/XIRR and CSV import/export; research checkpoints comparing actual changed facts.

This release does not implement every original platform wishlist item. Broker orders, options chains/Greeks, analyst forecasts, full SEPA research and automatic corporate-action reconciliation are not fabricated. Public website endpoints are best effort and can lag or fail. Source availability is not a commercial redistribution licence. No fake market data or company results are bundled.

## Build

JDK 17 including compiler tools, Android SDK 35, Build Tools 34.0.0:

```sh
./gradlew testDebugUnitTest assembleRelease
```

Unsigned output: `app/build/outputs/apk/release/app-release-unsigned.apk`.

To sign with the owner's separate private backup:

```sh
export ANDROID_HOME=/path/to/android-sdk
export BIGBULL_KEYSTORE=/private/path/bigbull-release.p12
export BIGBULL_PASSWORD_FILE=/private/path/key-password.txt
bash tools/sign-release.sh
```

Private release keys/passwords are **not included in the source archive**. `signing/release.lineage` is public certificate-rotation proof from the old development certificate to the private release key. APK v3 signing requires Android 9+. Preserve the private signing backup for future updates. The public `dev-signing/debug.keystore` is only for development builds. No Play Store publishing or physical-phone installation is claimed.

Do not uninstall the older app merely to upgrade, because uninstalling removes local data. Validation checks the signed upgrade lineage and the database migration; it is not a physical installation guarantee.

## Tests

`BIGBULL_LIVE=true` enables public-source and native UI checks. `BIGBULL_FULL_SCAN=true` enables all NSE constituent URLs, calendars and a full NIFTY 500 history/RS pass. The optional historical fixture test needs `BIGBULL_LIVE_FIXTURES`. Test-only prose/records are never shipped as app data. See `VALIDATION.md` and XML reports under `validation/` for completed results.

## Sources

- https://www.niftyindices.com/indices/equity/broad-based-indices/NIFTY-500
- https://nsearchives.nseindia.com/content/equities/EQUITY_L.csv
- https://upstox.com/developer/api-documentation/instruments/ — supported NSE/BSE instrument directories; no account/token needed for these published files.
- https://www.nseindia.com/companies-listing/corporate-filings-board-meetings
- https://www.nseindia.com/companies-listing/corporate-filings-actions
- https://www.nseindia.com/companies-listing/corporate-filings-annual-reports
- Yahoo Finance public price/history/financial endpoints; exchange identity and INR checks.
- Tickertape published MMI, credited in the app.
- Groww company-logo image CDN; original company trademarks.
- https://github.com/chrisbanes/haze/tree/1.1.1 — actual backdrop blur implementation (Apache 2.0). Reviewed Kyant0/AndroidLiquidGlass, not bundled. Not a claim of Apple's exact rendering.
- https://github.com/google/fonts/tree/main/ofl/cormorantgaramond — BB font, SIL OFL.
- https://jsoup.org — reader extraction, MIT.
- https://developer.android.com/tools/apksigner — signing/rotation.

Earlier Figma reference is the 0.6 direction, not a claim that this release is synchronized to that file. Native previews are test renders of the actual Compose implementation, not generated concepts.
