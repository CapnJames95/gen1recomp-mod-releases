# Disable L/R Help 0.1.0 validation

> **Historical validation record.** Counts, versions and pending-work statements below refer to the recorded test runs. For current package versions, installation status and latest checks, see [collection verification](https://github.com/CapnJames95/gen1recomp-mod-releases/blob/main/docs/VERIFICATION.md).


Target: official upstream `5540fc1538c7c9c8a3c8c85e09679ae03f28beaf`.

76 checks pass per edition (152 total), using the real Input, Help update and Game3 L=A code with a stubbed Help presenter. Tests cover keyboard and controller L/R edges and held states in boot/field/battle phases, direct Help requests, closing already-open Help, reset, previous-handler chaining, other-mod handled results, saved option preservation, L=A suppression/restoration, wrapper reload, inactive loader ownership and unsupported editions.

No player saves are used or changed. This is automated synthetic input, not physical controller/Android testing. Existing native menu actions remain possible and competing mods' hotkey assignments are not resolved. No custom UI is added.

Strict fixture validation, lint and Gen 3 checks pass (three unresolved dynamic module-passing sites are informational). Both-edition full collection suites pass 345 assertions each, including existing L hotkey routing. The collection initially failed an obsolete hardcoded QoL count after package removals; its assertion now counts installed core QoL packages and passes. This changes test bookkeeping, not Dual Screen runtime behavior.

Run from the engine checkout:

```sh
luajit /path/to/collection/tools/disable-lr-help/test.lua /path/to/collection firered
```

Repeat with `leafgreen`. Collection/modkit logs are under `outputs/disable-lr-help-0.1.0/`.
