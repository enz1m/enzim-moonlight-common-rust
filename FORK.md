# enzUI Moonlight Common Rust fork

Based on MrCreativ3001/moonlight-common-rust at
`a972937b2e84b21a6a390873930e3afe4cfa767d`, which remains the upstream Rust tip.
Upstream history, package identities and GPL-3.0 notices are preserved.

Separate changes:

- Disable the optional native diagnostic callback and remove the unused Rust
  variadic formatter so the native backend compiles on stable Rust.
- Keep the native connection claim until synchronous, idempotent shutdown has
  stopped workers and cleared callbacks. Drop never creates replacement streams
  or detached cleanup workers. Fallible startup retains the same ownership.
- Pin newer official native Common-C code and its upstream ENet/NanoRS submodules.
  Their original repositories and licenses are retained, without source copies.

Remote disables default features and uses `std,openssl,stream-c`. Its own bounded
HTTP implementation verifies paired server certificates. The upstream optional
ureq backend is unchanged and is not used or qualified by Remote; its permissive
certificate policy must not be treated as verified TLS support.
