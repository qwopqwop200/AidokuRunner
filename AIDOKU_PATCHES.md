# Aidoku patches

Branch `aidoku` of this fork is what the Aidoku app (qwopqwop200/Aidoku) builds
against. It starts from upstream https://github.com/Aidoku/AidokuRunner at
`2ed3f0d395be0c3ee9ebe238e2ffcead0094613f`.

- Sources run their `main.wasm` with the Wasm3 interpreter, as upstream.
  `Source` checks for cancellation around source calls, and genre filter lookup
  ignores option indices with no matching ID.
- Partial results are delivered only to the subscription that requested them;
  VarInt decoding rejects overlong input, and EpochDate
  throws instead of trapping on out-of-range dates.

Upstream notices are unchanged; README.md carries the copyright and
distribution terms. Run `swift test --jobs 2` after changing it, plus the app's
source/authentication suites.
