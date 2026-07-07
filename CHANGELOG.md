# Changelog

## v1.0.0

Initial release of the S7comm plugin.

- Six abilities mapped to ATT&CK for ICS: read/write data block (Read/Write Var),
  read CPU state, stop/start CPU, and read System Status List (SZL).
- Generic `s7comm_cli` payload (python-snap7) with PyInstaller build + cross-platform
  CI, and unit tests driving a local snap7 server.
- `S7comm Sample Facts` source and a payload registry.
- A GUI panel (splash service + Magma Vue view) and a read-db output parser that
  produces `s7comm.db.*` facts.
- Fieldmanual documentation in `docs/s7comm.md`.
