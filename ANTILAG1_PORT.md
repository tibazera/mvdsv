# Antilag 1 port scope

This branch ports the existing Antilag 1 server support to current
QW-Group/MVDSV. It preserves the current `sv_antilag 1` behaviour; this is
not a replacement design or a new balance model.

The port contains the extensions needed by the existing KTX CSQC and ezQuake
implementation: accurate timings, weapon prediction, simple projectiles,
EZCSQC negotiation and the required runtime hooks.

## Compatibility contract

When a server selects `sv_antilag 1` and the client negotiates the required
capabilities, the resulting gameplay must match the current KTX Antilag 1
stack. Clients without those capabilities must fall back safely to
the existing non-Antilag-1 path.
