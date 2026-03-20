## Hi, I'm Vanderhell 👋

Embedded systems developer focused on **industrial IoT**, Modbus, MQTT, and building reliable firmware.
I write small, focused C/C# libraries that solve real problems — zero dependencies, zero allocations, tested.

---

### 🔧 micro-toolkit — Modular C99 libraries for embedded systems

A collection of composable libraries that share a common philosophy: **no heap, no dependencies, no code generation — just `#include` and go.**

```
┌─────────────────────────────────────────────────────────────┐
│  microsh ─── debug shell        microlog ── structured logging
│  microfsm ── state machines     microres ── retry + breaker
│  microconf── flash config       microcbor── CBOR serialization
│  micoring ── ISR-safe ring buf  iotspool ── MQTT persistence
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

**[→ micro-toolkit](https://github.com/Vanderhell/micro-toolkit)** — architecture overview, design philosophy, and a complete example project using all 7 libraries together

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

---

### 🏭 Industrial IoT & protocols

Desktop tools and firmware for real-world industrial communication.

| Project | Description |
|---------|-------------|
| [IOBusMonitor](https://github.com/Vanderhell/IOBusMonitor) | Multi-protocol desktop tool for Modbus TCP/RTU and Siemens S7 PLCs — live dashboard, history charts, SQLite archive |
| [RTULogSuite](https://github.com/Vanderhell/RTULogSuite) | Complete Modbus RTU logging toolchain — ESP32 firmware + Windows visualization app |
| [iotspool](https://github.com/Vanderhell/iotspool) | Persistent store-and-forward MQTT queue — survives power loss, C99, zero dependencies |

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
