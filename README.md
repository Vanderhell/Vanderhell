## Hi, I'm Vanderhell 👋

Embedded systems developer focused on **industrial IoT**, Modbus, MQTT, and building reliable firmware.
I write small, focused C/C# libraries that solve real problems — zero dependencies, zero allocations, tested.

---

### 🗄️ loxdb — Deterministic embedded database for MCU/edge systems

![loxdb banner](https://github.com/Vanderhell/loxdb/raw/refs/heads/master/docs/banner.svg)

A compact embedded database written in **C99** for firmware and small edge runtimes. `loxdb` combines **key-value**, **time-series**, and **small relational tables** behind one API surface, with **a single allocation at init**, **fixed RAM budgeting**, and an optional **WAL-backed** persistence path for **power-fail recovery**.
It is designed for embedded products that need predictable memory use, durable state, and a much smaller integration surface than a general SQL database.

**Current scope:** KV with optional TTL, time-series streams with retention/overflow policies, and fixed-schema relational tables with one indexed column per table.
**Licensing:** the current repository is the **MIT-licensed Free Edition**. A paid extension, **loxdb_pro**, is currently in development and is planned as a separate commercial add-on.

| Project | Description | Tech |
|---|---|---|
| [**loxdb**](https://github.com/Vanderhell/loxdb) | Deterministic embedded database for constrained systems and microcontrollers. Supports key-value records, time-series streams, and small relational-style tables, using a single allocation at initialization and optional WAL-backed persistence. | C99 |

### 🔧 micro-toolkit — Modular C99 libraries for embedded systems

A collection of composable libraries that share a common philosophy: **no heap, no dependencies, no code generation — just `#include` and go.**

```
┌─────────────────────────────────────────────────────────────┐
│  microsh ─── debug shell        microlog ── structured logging
│  microfsm ── state machines     microres ── retry + breaker
│  microconf── flash config       microcbor── CBOR serialization
│  micoring ── ISR-safe ring buf  iotspool ── MQTT persistence
│  microtimer─ software timers    microbus ── event pub/sub
└─────────────────────────────────────────────────────────────┘
```

| Library | What it does | Tests |
|---------|-------------|-------|
| [microfsm](https://github.com/Vanderhell/microfsm) | Table-driven finite state machine engine | 36 |
| [microres](https://github.com/Vanderhell/microres) | Retry with backoff, circuit breaker, rate limiter | 41 |
| [microconf](https://github.com/Vanderhell/microconf) | Schema-driven config with CRC + flash storage | 40 |
| [microlog](https://github.com/Vanderhell/microlog) | Multi-backend structured logging | 33 |
| [microsh](https://github.com/Vanderhell/microsh) | Debug shell with history + tab completion | 43 |
| [microcbor](https://github.com/Vanderhell/microcbor) | Minimal CBOR encoder/decoder (RFC 8949) | 43 |
| [micoring](https://github.com/Vanderhell/micoring) | Generic lock-free SPSC ring buffer | 33 |
| [microtimer](https://github.com/Vanderhell/microtimer) | Software timer manager — oneshot + periodic, drift-corrected | 25 |
| [microbus](https://github.com/Vanderhell/microbus) | Event pub/sub bus — topic-based, ISR-safe deferred queue | 34 |

**[→ micro-toolkit](https://github.com/Vanderhell/micro-toolkit)** — architecture overview, design philosophy, and a complete example project

---

### 🔗 embedded-guard — Safety, monitoring & recovery

Libraries that bridge the toolkit together: boot orchestration, health monitoring, watchdogs, panic handling, OTA updates.

| Library | What it does | Tests |
|---------|-------------|-------|
| [microhealth](https://github.com/Vanderhell/microhealth) | Runtime health monitor — collect metrics, dual thresholds, edge-triggered alerts | 32 |
| [microwdt](https://github.com/Vanderhell/microwdt) | Per-task software watchdog — kick-based liveness, OK → LATE → STARVED escalation | 33 |
| [microboot](https://github.com/Vanderhell/microboot) | Boot & recovery manager — crash loop detection, proven boot pattern, boot reason tracking | 32 |
| [microassert](https://github.com/Vanderhell/microassert) | Unified panic system — hook chain (log → dump → reset), four severities, re-entrancy guard | 33 |
| [microota](https://github.com/Vanderhell/microota) | OTA firmware update — chunked download, CRC verify, version check, commit/rollback | 27 |
| [microflash](https://github.com/Vanderhell/microflash) | Unified flash abstraction — partitions, NOR/EEPROM/FRAM/RAM, erase-write, wear stats | 33 |

---

### 🛡️ Bare-metal safety & diagnostics

Small utilities for writing safer, more debuggable embedded C code.

| Project | Description |
|---------|-------------|
| [panicdump](https://github.com/Vanderhell/panicdump) | Crash dump library for Cortex-M3/M4 — capture on fault, survive reboot, decode offline |
| [MCU-Malloc-Tracker](https://github.com/Vanderhell/MCU-Malloc-Tracker) | Deterministic heap diagnostics for bare-metal MCUs — malloc/free tracking, CRC snapshots |
| [nvlog](https://github.com/Vanderhell/nvlog) | Power-loss safe append log for FRAM/EEPROM/NOR flash — no heap, no filesystem, 186 tests |
| [defer](https://github.com/Vanderhell/defer) | Automatic resource cleanup for C via `DEFER()` macro — single header, GCC/Clang/ARM |
| [cguard](https://github.com/Vanderhell/cguard) | Scope guards and result types for C — auto cleanup (free, fclose, unlock), header-only |
| [safemath](https://github.com/Vanderhell/safemath) | Overflow-checked add, mul, align and buffer sizing — single header, C99 |
| [microcrypt](https://github.com/Vanderhell/microcrypt) | SHA-256, HMAC-SHA256, AES-128 ECB/CBC — NIST/RFC test vectors, zero dependencies |
| [microdh](https://github.com/Vanderhell/microdh) | Minimal X25519 (Curve25519) key exchange for embedded systems — RFC 7748, zero dependencies, zero allocations |
| [microtest](https://github.com/Vanderhell/microtest) | Single-header test framework — suites, fixtures, filtering, color output, 16 assertion macros |

---

### 📦 Binary formats & data engines

| Project | Description |
|---------|-------------|
| [num8](https://github.com/Vanderhell/num8) | O(1) membership engine for 8-digit numbers — 12.5 MB fixed bitset, 124M lookups/s, C99, zero dependencies |
| [IronFamily.FileEngine](https://github.com/Vanderhell/IronFamily.FileEngine) | Binary IoT file engines — ICFG (schema-validated config), ILOG (structured append log), IUPD (firmware update package) — .NET + native C |

---

### 🏭 Industrial IoT & protocols

Desktop tools and firmware for real-world industrial communication.

| Project | Description |
|---------|-------------|
| [IOBusMonitor](https://github.com/Vanderhell/IOBusMonitor) | Multi-protocol desktop tool for Modbus TCP/RTU and Siemens S7 PLCs — live dashboard, history charts, SQLite archive |
| [RTULogSuite](https://github.com/Vanderhell/RTULogSuite) | Complete Modbus RTU logging toolchain — ESP32 firmware + Windows visualization app |
| [iotspool](https://github.com/Vanderhell/iotspool) | Persistent store-and-forward MQTT queue — survives power loss, C99, zero dependencies |
| [uMesh](https://github.com/Vanderhell/uMesh) | Lightweight mesh networking stack for ESP32 over raw 802.11 — multi-hop routing, encrypted transport, compact custom protocol |
| [num8lup](https://github.com/Vanderhell/num8-lup) | Low-bandwidth update propagation protocol for NUM8 datasets — async sender/receiver split, delta streams over LoRa-style constrained links, C99 |

---

### 🖥️ Desktop & .NET

| Project | Description |
|---------|-------------|
| [MultiGpuHelper](https://github.com/Vanderhell/MultiGpuHelper) | C# library for scheduling compute workloads across multiple GPUs — device discovery, VRAM budgeting, policy-based selection |
| [CrudFramework](https://github.com/Vanderhell/CrudFramework) | Lightweight CRUD framework for .NET (EF Core + SQLite/SQL Server) — validation, filtering, paging, WPF-ready bindings |

---

### ⚡ Hardware projects

| Project | Description |
|---------|-------------|
| [securebox-hw](https://github.com/Vanderhell/securebox-hw) | Secure hardware password manager on ESP32-S3 with external encrypted storage |
| [Pragotron-Controller](https://github.com/Vanderhell/Pragotron-Controller) | Minute-impulse controller for a Pragotron stepper clock — ESP32, DS1307 RTC, H-bridge |
