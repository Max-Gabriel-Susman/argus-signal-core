# argus-signal-core

Portable `no_std` Rust core for Argus biosignals: HRV, sleep staging, and circadian smart-wake timing, with Kotlin bindings via UniFFI.

It turns the beat-to-beat intervals and motion that a wearable records into sleep-stage estimates, and decides when to wake someone inside a wake window: at a light-sleep moment rather than in deep sleep, with the window placed by circadian phase. The same code runs on the watch, through the bindings, and on a desktop, where recorded nights replay through it as tests.

## Status

Scaffolding. The workspace and its three crates exist. The algorithms come next, starting with cleaning inter-beat intervals and computing RMSSD.

## Crates

| Crate | Path | Kind | Role | State |
| --- | --- | --- | --- | --- |
| `argus_signal_core` | `crates/core` | `no_std` library | IBI cleaning, HRV, motion, sleep staging, wake decision | Placeholder |
| `argus_signal_ffi` | `crates/ffi` | Library | UniFFI bindings for Kotlin (Swift later); builds the shared library the Android apps load | Placeholder |
| `argus_signal_replay` | `crates/replay` | Binary | Replays recorded nights through the core on a desktop | Placeholder |

Only `argus_signal_core` is `no_std`. It depends on nothing that needs an operating system, so the same code can run on a phone, a watch or a microcontroller. The bindings and the replay tool use `std`, which is why they are separate crates.

## Build and test

```bash
cargo build
cargo test
cargo run -p argus_signal_replay
```

The Android apps that use it live in [argus-android](https://github.com/Max-Gabriel-Susman/argus-android).

## License

Apache-2.0. See [LICENSE](LICENSE).
