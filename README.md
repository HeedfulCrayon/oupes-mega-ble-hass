# OUPES Mega — Home Assistant Integrations

Custom Home Assistant integrations for **OUPES Mega** power stations — fully
local, no cloud dependency required. Supports both **Bluetooth (BLE)** and
**WiFi** communication channels.

---

## Integrations

This repo contains two custom components that can be installed independently
depending on your setup:

### 1. BLE Integration (`oupes_mega_ble`)

**Direct Bluetooth connection** — the simplest setup. Connects to your OUPES
device over BLE and exposes sensors, switches, and settings entities.

- No network infrastructure needed — just a Bluetooth adapter on your HA server
- Continuous or polled connection modes
- Supports BLE pairing (no Cleanergy app/cloud needed)
- Device control: toggle AC/DC/USB outputs, adjust settings

**[Full documentation →](custom_components/oupes_mega_ble/README.md)**

The BLE integration can be installed through HACS as a custom repository. Add
`https://github.com/HeedfulCrayon/oupes-mega-ble-hass` in **HACS → Integrations
→ Custom repositories**, select **Integration**, and install **OUPES Mega BLE**.

---

## Quick Start (BLE)

1. Install **OUPES Mega BLE** through HACS, or copy
	`custom_components/oupes_mega_ble/` into your HA config directory.
2. Restart Home Assistant.
3. Power on the OUPES device and press the IoT button (indicator flashes).
4. HA auto-discovers the device — click the notification to set up.
5. Choose **Create New Key** (factory-reset the device first: hold IoT 5 s).

---

## Supported Models

| Series | Models |
|--------|--------|
| **Mega** | Mega 1, Mega 2, Mega 3, Mega 5 |
| **Exodus** | Exodus 1200, Exodus 1500, Exodus 2400, S024 Lite, S1 Lite |
| **Guardian** | Guardian 6000, HP2500, D5 V2 |
| **Other** | S2 V2, DC 800, LP350, LP700, PB300, UPS 1200, UPS 1800 |

Model-specific features (settings, entity names) are applied automatically
based on the BLE product ID.

---

## Protocol Documentation

See [`debug_info/README.md`](debug_info/README.md) for the complete
reverse-engineered protocol reference, covering:

- BLE GATT profile, pairing/claiming protocol, packet format
- WiFi TCP broker protocol, streaming activation sequence
- Telemetry attribute map (shared across BLE and WiFi)
- Cloud API endpoints (HTTP REST + SiBo)
- Device firmware boot sequence

## Debug Tools

The [`debug_info/`](debug_info/) directory contains standalone tools:

| Script | Purpose |
|--------|---------|
| `pair_device.py` | BLE pairing + WiFi provisioning |
| `scan_ble.py` | Live BLE telemetry scanner |
| `parse_btsnoop.py` | Parse Android btsnoop HCI logs |
| `probe_key.py` | Test candidate device keys |
| `ble_diag.py` | BLE GATT diagnostics |
| `provision_wifi.py` | Send WiFi credentials to paired device |
| `scan_wifi_ports.py` | Scan device for open network ports |
| `analyze_attr_csv.py` | Analyze BLE attribute debug logs |

---

## License

See [LICENSE](LICENSE).
