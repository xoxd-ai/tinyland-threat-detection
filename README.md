# @tummycrypt/tinyland-threat-detection (retired)

This repository is retired and archived (2026-10-14, estate uplift rulings
RU2, RU6, RU7, RU8).

Its code now lives in
[xoxd-ai/tinyland-security](https://github.com/xoxd-ai/tinyland-security) as
the `./threat-detection` subpath export of `@tummycrypt/tinyland-security`,
starting with tinyland-security 1.1.0. The API is unchanged:
`configureThreatDetection`, `getThreatDetectionConfig`,
`resetThreatDetectionConfig`, `getLogger`, `getHaversineDistance`,
`ThreatCorrelationService`, `SecurityDataService` and all of this package's
exported types.

## Migrating

1. In `MODULE.bazel`, replace
   `bazel_dep(name = "tummycrypt_tinyland_threat_detection", ...)` with
   `bazel_dep(name = "tummycrypt_tinyland_security", version = "1.1.0")`
   from [xoxd-ai/bazel-registry](https://github.com/xoxd-ai/bazel-registry),
   and link `@tummycrypt_tinyland_security//:pkg` with `npm_link_package`.
2. Change imports (and `vi.mock` targets) from
   `@tummycrypt/tinyland-threat-detection` to
   `@tummycrypt/tinyland-security/threat-detection`.
3. tinyland-security 1.x is built with TypeScript 7.0.2 (RU1); move the
   consumer to the same stack in the same change.

The registry module `tummycrypt_tinyland_threat_detection` is marked
deprecated. Its 0.2.2 and 0.2.3 entries stay resolvable and nothing is
yanked, so existing pins keep building until they move. The package is no
longer published to npm or GitHub Packages; the publish workflow is removed.
