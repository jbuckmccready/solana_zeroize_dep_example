Example showing `zeroize` transitive dependency problem caused by Solana dependencies.

`async-nats` depends on `signatory` which depends on `zeroize = "^1.4"`. `curve25519-dalek` `v3.x`
depends on `zeroize = ">=1, <1.4"` and `aes-gcm-siv` `v0.10.x` depends on `zeroize = ">=1, <1.4"`.

Try to run `cargo build` or `cargo check` and you'll see the conflict that arises.

Updating `curve25519-dalek` to `v4.x` and `aes-gcm-siv` to `v0.11.x` will eliminate the problem of
depending on `zeroize = "<1.4"`.

Created as an example for this issue: https://github.com/solana-labs/solana/issues/26688
