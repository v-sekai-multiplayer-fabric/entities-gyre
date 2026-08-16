# Provenance

Moved out of `README.md`, which is capped at 40 lines. Unchanged apart from the
names RFD 0111 retired.

## How the Gyre supplies what the design needed

Four things the ladder had to invent, the setting already had:

| the design needed | the Gyre already has |
|---|---|
| a decay sink on capability, or everyone ends up able to do everything | Frames seize up without parts |
| temporal pressure that is not an arbitrary tick budget | the Debt Clock |
| access as a hard obstacle rather than a social nicety | Sparks are legally owned property, and debt-collection is automated |
| a reason distances are vast and coordinates large | a failing ring-station around a gas giant |

The last one is why the engine is built at `precision=double`: single precision
holds sub-millimetre resolution only to about 8 km from origin, and the authority
advances every Spark in one coordinate space at 20 Hz, so there is no per-client
origin to rebase around.

## Provenance

Moved from `V-Sekai-fire/turboquant-project`, which is retired. The llama.cpp
carrying TurboQuant KV and MTP lives in `V-Sekai-fire/datasource-llama-cpp`;
inference belongs to the server, never to the engine.

## Salvage from turboquant-ws

That workspace is retired and its contents are not backed up, so anything worth
keeping was moved here rather than left to be deleted.

| path | what it is |
|---|---|
| `docs/llm-integration-notes.md` | the turboquant-godot integration record: subtree provenance, the TurboQuant fork surface, MTP status, push authority, and where inference is allowed to run |
| `docs/llama-cpp-patches/` | the two Godot-local llama.cpp patches, kept as a record of changes already applied — not to be applied again |
| `sim/check_claims.py` | the falsifiable-claims gate written against turboquant-godot |

`check_claims.py` is kept for its **shape**, not its assertions, which are about
a tree that is retiring. Its one durable lesson: it reported 7 checked / 0 failed
on a tree that did not compile, because it verified metadata and never asked
whether the thing built. A gate that cannot fail on the most basic property is
the decoration its own docstring warns about. Any gate that replaces it starts
with "does it build".

Still live elsewhere, deliberately not copied:

- `V-Sekai-fire/datasource-llama-cpp` — llama.cpp with TurboQuant KV and MTP
- `V-Sekai-fire/godot-build-scripts` @ `double-precision-and-fork-source` —
  `GODOT_PRECISION` and `GODOT_REPO` knobs, both defaulting to upstream
- `V-Sekai-fire/build-containers` — forked, unmodified
- `v-sekai-multiplayer-fabric/contract-bus` @ `linux-command-proof` — the
  command/reply loop proved on Linux, 8/8 round trips, plus the `lib`/`lib64`
  fix without which the shipped image cannot dlopen iceoryx2 at all
- `weftspun/logbook` — the measurement entry and its retraction
