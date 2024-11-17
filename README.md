# Blahaj

[![Crates](https://img.shields.io/crates/v/blahaj.svg)](https://crates.io/crates/blahaj)
[![Docs](https://docs.rs/blahaj/badge.svg)](https://docs.rs/blahaj)

Fast, small and secure [Shamir's Secret Sharing](https://en.wikipedia.org/wiki/Shamir%27s_Secret_Sharing) library crate

Documentation:
-    [API reference (docs.rs)](https://docs.rs/blahaj)

## Usage

Add this to your `Cargo.toml`:

```toml
[dependencies]
blahaj = "0.6"
```

If your environment doesn't support `std`:

```toml
[dependencies]
blahaj = { version = "0.6", default-features = false }
```

To get started using Blahaj, see the [Rust docs](https://docs.rs/blahaj)

## Features

### Developer friendly
The API is simple and to the point, with minimal configuration.

### Fast and small
The code is as idiomatic and clean as possible, with minimum external dependencies.

### Secure by design
The implementation forbids the user to choose parameters that would result in an insecure application,
like generating more shares than what's allowed by the finite field length.

## Limitations

Because the Galois finite field it uses is [GF256](https://en.wikipedia.org/wiki/Finite_field#GF(p2)_for_an_odd_prime_p),
only up to 255 shares can be generated for a given secret. A larger number would be insecure as shares would start duplicating.
Nevertheless, the secret can be arbitrarily long as computations are performed on single byte chunks.

## Testing

This crate contains both unit and benchmark tests (as well as the examples included in the docs).
You can run them with `cargo test` and `cargo bench`.

### Benchmark results [min mean max]

| CPU                                       | obtain_shares_dealer            | step_shares_dealer              | recover_secret                  | share_from_bytes                | share_to_bytes                  |
| ----------------------------------------- | ------------------------------- | ------------------------------- | ------------------------------- | ------------------------------- | ------------------------------- |
| Intel(R) Core(TM) i7-8550U CPU @ 1.80GHz  | [1.4321 us 1.4339 us 1.4357 us] | [1.3385 ns 1.3456 ns 1.3552 ns] | [228.77 us 232.17 us 236.23 us] | [24.688 ns 25.083 ns 25.551 ns] | [22.832 ns 22.910 ns 22.995 ns] |
| Intel(R) Core(TM) i7-8565U CPU @ 1.80GHz  | [1.3439 us 1.3499 us 1.3562 us] | [1.5416 ns 1.5446 ns 1.5481 ns] | [197.46 us 198.37 us 199.22 us] | [20.455 ns 20.486 ns 20.518 ns] | [18.726 ns 18.850 ns 18.993 ns] |
| Apple M1 ARM (Macbook Air)                | [3.3367 us 3.3629 us 3.4058 us] | [741.75 ps 742.65 ps 743.52 ps] | [210.14 us 210.23 us 210.34 us] | [27.567 ns 27.602 ns 27.650 ns] | [26.716 ns 26.735 ns 26.755 ns] |

# Contributing

If you find a vulnerability, bug or would like a new feature, reach out to
<mailto:team@distrust.co>.

# License

Blahaj is distributed under the terms of the MIT license.

See [LICENSE-MIT](LICENSE-MIT) and [COPYRIGHT](COPYRIGHT) for details.
