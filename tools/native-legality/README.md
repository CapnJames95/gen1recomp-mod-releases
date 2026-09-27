# Native generation compatibility tests

Canonical shared correction: `native_legality.lua`. Each of the six affected mods ships an identical copy. `loader_test.lua` exercises the real SDK package loader; `with-fixes.lua` enables the same correction around the representative generation probes.

Run from the collection root:

```sh
python3 tools/native-legality/run.py --engine /tmp/frlg-dual-upstream --lua /tmp/daycare-luajit/src/luajit --cache-root '/path/to/pokemon-love2d' --output /tmp/mod-legality-fixed
python3 tools/native-legality/regression.py
```

The regression script contains the local engine, interpreter and imported-cache paths used for this run; adjust these for another machine. The engine checkout needs `functional_collection` pointing to this collection, `mods/examples/shiny_hunter` and `mods/examples/legalmon` pointing to their respective source folders, and `mod/frlg_dual_screen` pointing to the Dual Screen source folder. Imported FireRed and LeafGreen data must already exist.

Build the record checker in `../legality-pass/checker` and complete-save checker in `check-saves` using .NET 10 and `-p:PKHeXCorePath=/absolute/path/PKHeX.Core.dll`. Run each resulting `Check.dll` with `/tmp/mod-legality-fixed/samples` as its argument. The record checker validates the emitted encrypted `.pk3` files; the independent save checker parses each `.sav`, validates save checksums and checks every nonempty party/box entry.

The recorded run used PKHeX.Core 26.8.26.0, SHA-256 `8ea6be35197db5d0a5911a72210c876804827efff00359a5f242bbb71add0375`. Generated Pokémon and saves stay outside the repository. Results and per-suite logs are in `results`; `pkhex-initial.jsonl` is a superseded debugging run, while `pkhex-fixed.jsonl` and `pkhex-saves.jsonl` are final results.
