# Aidoku patches

Branch `aidoku` of this fork is what the Aidoku app (qwopqwop200/Aidoku) builds
against. It starts from upstream https://github.com/Aidoku/AidokuRunner at
`2ed3f0d395be0c3ee9ebe238e2ffcead0094613f`.

- The Wasm3 interpreter and its imports are kept but unused: `Source` only
  uses a native runner registered by exact source ID and version, and source
  executables are never read or executed. Unsupported sources are rejected.
- Metadata decoding, Postcard serialization and task-owned partial-result
  publication are kept; VarInt decoding rejects overlong input, and EpochDate
  throws instead of trapping on out-of-range dates.

Upstream notices are unchanged; README.md carries the copyright and
distribution terms. Run `swift test --jobs 2` after changing it, plus the app's
source/authentication suites.
