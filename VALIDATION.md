# Bigbull 1.1 validation — 3 November 2026

Version 1.1.0 (code 12), package com.bigbull.research, Android 9+, target SDK 35. The release build completed with release lint, R8 optimization and resource shrinking. The manifest is non-debuggable.

APK SHA-256: `6773376d1bbb3a53250c6acfd0d7eaf985f2731bc4e66fc17c32f87907378408`.

## Completed checks

- 73 automated tests: 65 passed, 8 optional tests skipped, zero failures/errors. XML results and build log are in validation/1.1.
- New checks cover strong buy/strong sell/neutral and insufficient-history ratings, actual Compose barometer rendering and expandable signals, private journal persistence per stock, journal export, ET image identity and promotion/audio removal, and ET inline prose normalization.
- Real downloaded ET and NDTV Profit article HTML samples parsed successfully with readable text and publisher images. The live NDTV business feed returned 20 entries. These are point-in-time checks; publisher content and access can change. Downloaded article HTML is not included in the source or APK.
- Existing regression coverage includes technical/fundamental calculations, Minervini rules, universes, calendars, annual-report metadata, portfolio/storage migration, native navigation and article error/loading states.
- Signed APK verified independently on API levels 28–37. The release certificate is unchanged from 1.0; the original development-to-release certificate rotation lineage and installed-data capability were verified. Alignment and manifest checks passed.

## Validation scope

Physical-device installation and native PDF rendering were not tested in this environment. The optional full NIFTY 500/BSE scan and live-source suite were not rerun; eight optional tests were skipped. Source timestamps and missing/error states remain explicit.

Earlier validation folders contain earlier-version results and are not counted in the 1.1 total. No fictional market records are bundled. Synthetic data is confined to tests.
