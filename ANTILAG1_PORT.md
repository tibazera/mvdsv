# Antilag 1 port scope

This branch ports the existing Dusty Antilag 1 server support to current
QW-Group/MVDSV.  It preserves the current `sv_antilag 1` behaviour; this is
not a replacement design or a new balance model.

The port contains the extensions needed by the existing KTX CSQC and ezQuake
implementation: accurate timings, weapon prediction, simple projectiles,
EZCSQC negotiation and the required runtime hooks.

## Explicit non-goals

No player spray decal feature belongs in this branch.  It must not compile or
advertise spray support, and it must not add `sv_sprays.c`, `clc_spray`,
`svc_spray`, `MVD_PEXT1_SPRAYS`, or spray cvars.

The spray extension is protocol-distinct from Antilag 1.  A future feature
branch may propose it separately, build-disabled by default and only exposed
when explicitly enabled.  Its absence must not affect Antilag 1.

## Compatibility contract

When a server selects `sv_antilag 1` and the client negotiates the required
capabilities, the resulting gameplay must match the current Dusty/KTX
Antilag 1 stack.  Clients without those capabilities must fall back safely to
the existing non-Antilag-1 path.
