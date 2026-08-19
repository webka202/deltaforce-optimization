# Delta Force Optimization

One-click service control, RAM cleanup and anti-stutter boost for Delta Force on Windows. English / 한국어 interface.

[Delta Force Optimization]

## Quick start

1. Download `DeltaForce Optimization v1.1.0.exe`
2. Run it — accept the UAC prompt (administrator rights are required)
3. No installation needed

## What it does

| Feature | Description |
|---|---|
| **Service control** | Grid of 61 services commonly disabled for gaming. Start/stop per service or all at once; running services are listed first. |
| **OPTIMIZATION** | Big one-click button: stops all configured services, flushes RAM, then shows exactly how much memory was freed. |
| **PERFORMANCE BOOST** | Anti-stutter pack in one pass. |
| **RESTORE** | Reverts everything PERFORMANCE BOOST changed. Also runs automatically when the app is closed. |
| **Find issues** | Searches today's Application event log for Critical/Error events mentioning Delta Force, with a one-click Google search per result. |
| **Launch Delta Force** | Starts the game from `C:\Delta Force\launcher\df_launcher_global.exe` |
| **한국어 / English** | Full language toggle in the top-right corner. |

## PERFORMANCE BOOST

Clicking PERFORMANCE BOOST applies four fixes for stutter and lag:

1. **Ultimate Performance power plan** — activates the Windows Ultimate Performance scheme (registered automatically if missing; falls back to High performance). Your previous plan is remembered.
2. **GPU persistence mode** (NVIDIA) — keeps the GPU driver resident via `nvidia-smi` so it never re-initializes between loads.
3. **Timer resolution 0.5 ms** — smoother frame pacing, held while the app runs.
4. **RAM monitor** — watches free memory; if it drops below ~2 GB it re-runs the cleaner and reports `RAM MONITOR: +X MB FREED` (15-second cooldown).

**RESTORE** (or simply closing the app) puts everything back: previous power plan, previous timer resolution, GPU persistence mode off, monitor stopped.

### AMD users

AMD has no supported command-line automation, so the app shows in-app guidance instead: open AMD Software: Adrenalin Edition and set the graphics profile to Gaming or eSports.

## Requirements

- Windows 10 / 11 x64 
- Administrator rights
- Delta Force installed at the default launcher path above for the Launch button

## SmartScreen & antivirus false positives

The app is **currently unsigned**, so Windows and some antivirus engines may warn about it.

- **SmartScreen** ("Windows protected your PC"): click **More info**, then **Run anyway**.
- **Antivirus** may flag it as a false positive

## Safety

- **No registry keys are written at any point.** All changes use `powercfg`, `nvidia-smi` and documented Windows APIs.
- The app never disables antivirus and never force-kills tasks.
- If the process is force-killed, timer resolution resets automatically on reboot; the power plan stays active until you switch it back.
- Stopping services is reversible — use Start all to bring everything back at any time.
