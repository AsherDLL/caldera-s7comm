# S7comm Plugin for Caldera

The S7comm plugin provides [Caldera](https://github.com/mitre/caldera) with
adversary-emulation abilities for the **Siemens S7 (S7comm)** protocol (ISO-on-TCP,
port 102), used by S7-300/400/1200/1500 PLCs.

Abilities are mapped to [ATT&CK for ICS](https://attack.mitre.org/matrices/ics/) and
driven by a generic command-line client (`s7comm_cli`, built on python-snap7), so
they work against any S7 CPU, the target address, rack/slot, and DB numbers are
supplied as facts.

## Abilities

| Ability | Tactic | Technique |
|---|---|---|
| S7comm - Read Data Block | Collection | T0801 Monitor Process State |
| S7comm - Read CPU State | Collection | T0801 Monitor Process State |
| S7comm - Write Data Block | Impair Process Control | T0836 Modify Parameter |
| S7comm - Stop CPU | Inhibit Response Function | T0816 Device Restart/Shutdown |
| S7comm - Start CPU | Execution | T0816 Device Restart/Shutdown |
| S7comm - Read System Status List | Discovery | T0846 Remote System Discovery |

See [`docs/s7comm.md`](docs/s7comm.md) for commands and the fact reference.

## Installation

1. Clone into Caldera's `plugins/` directory as `s7comm`:

   ```
   git clone https://github.com/AsherDLL/caldera-s7comm plugins/s7comm
   ```

   The payload binaries ship in `payloads/` (`s7comm_cli`, `s7comm_cli.exe`,
   `s7comm_cli_darwin`).

2. Enable the plugin in `conf/local.yml`:

   ```yaml
   plugins:
     - s7comm
   ```

3. Restart Caldera. Abilities appear under the tactics above, with an
   **S7comm Sample Facts** source to seed a fact source.

## Payload

`s7comm_cli` wraps [python-snap7](https://github.com/gijzelaerr/python-snap7),
which bundles the LGPL-3.0 `snap7` library. Source and build tooling are in `src/`;
see [`src/README.md`](src/README.md). The plugin is Apache-2.0.

## Tests

```
pip install -r src/requirements.txt pytest
PYTHONPATH=src python -m pytest tests -q
```

## License

Apache-2.0. See [`LICENSE`](LICENSE) and [`NOTICE.md`](NOTICE.md).

## Authors

- Asher Davila ([AsherDLL](https://github.com/AsherDLL))
- Malav Vyas ([MalavVyas](https://github.com/MalavVyas))
