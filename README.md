## Hi, I'm Vanderhell 👋

Industrial software and embedded systems developer focused on reliable tools for production, firmware, diagnostics, and edge systems.

I build small, focused C/C#/C++ libraries and applications for real-world use: embedded storage, runtime safety, industrial communication, monitoring, data acquisition, and practical AI-assisted development workflows.

My usual design bias:

- predictable behavior
- small integration surface
- clear failure modes
- zero or minimal dependencies
- tests before claims
- tools that solve real problems, not demo problems

---

## Collaboration

I am currently looking for collaborators who can help with testing, hardware validation, examples, documentation review, and real-world feedback on embedded C projects.

Main areas:

- embedded C testing
- MCU hardware validation
- storage and power-loss testing
- reliability and diagnostics
- industrial/edge use cases
- examples and integration feedback

If you are working with firmware, MCU platforms, RTOS/bare-metal systems, or industrial devices and want to test or review any of these projects, feel free to reach out.

## Main projects

### 🗄️ loxdb — Deterministic embedded database for MCU/edge systems

![loxdb banner](https://github.com/Vanderhell/loxdb/raw/refs/heads/master/docs/banner.svg)

[`loxdb`](https://github.com/Vanderhell/loxdb) is a compact embedded database written in **C99** for firmware and small edge runtimes.

It combines three storage models behind one API surface:

- **KV** for configuration, cache entries, and TTL-backed state
- **Time-series** for sensor samples and rolling telemetry
- **Relational fixed-schema tables** for small indexed structured data

Core design:

- one allocation at `lox_init()`
- fixed RAM budgeting
- zero external dependencies
- RAM-only or storage-backed operation
- optional WAL-backed persistence and recovery
- embedded-first storage HAL

`loxdb` is not a tiny SQLite clone. SQLite is excellent, but targets a different operating point. `loxdb` is intentionally narrower: deterministic storage for constrained firmware, dataloggers, controllers, and small edge runtimes where predictable memory and a small integration surface matter more than SQL features.

**License:** MIT open-source core.  
**Commercial extension:** [`loxdb_pro_docs`](https://github.com/Vanderhell/loxdb_pro_docs) contains public API-level documentation for the planned/commercial PRO module set.

---

### 🧩 loxdb_pro — Commercial production modules around loxdb core

[`loxdb_pro_docs`](https://github.com/Vanderhell/loxdb_pro_docs) documents the public integration-facing API for the commercial `loxdb_pro` layer.

The PRO layer is designed for embedded products that need more than storage:

- security and integrity
- runtime safety validation
- metrics, logging, monitoring, and alerting
- policy gates, quotas, retention, and scheduling
- backup and schema migration
- replication and transport framing
- OTA planning and rollback hooks
- CLI tooling
- optional SD card and NAND/FTL adapters

The public repository intentionally contains documentation only. The implementation and proprietary validation procedures are not published there.

---

### 🛡️ loxguard — Guard Blocks for embedded C firmware

[`loxguard`](https://github.com/Vanderhell/loxguard) is a lightweight **C99 guard-runtime** for embedded C.

It introduces **Guard Blocks** and **Checked Guard Blocks**: explicit execution boundaries around risky code such as parsers, protocol handlers, optional modules, and recovery-sensitive routines.

Instead of only failing with an assert or watchdog reset, `loxguard` turns failures into structured runtime evidence:

- lifecycle events
- policy decisions
- blackbox records
- reports
- CSV/KV import-export paths
- optional persistence and ecosystem adapters

Current scope includes checked span/arena primitives, Guard Block lifecycle tracking, failure reporting, policy decisions, local blackbox evidence, and host-tested integration paths.

`loxguard` does not claim full memory safety for arbitrary C code and is not a safety-certified framework. Its value is narrower: make unsafe execution states easier to detect, record, and react to in small embedded C systems.

---

## Project map

| Project | Description | Tech |
|---|---|---|
| [loxdb](https://github.com/Vanderhell/loxdb) | Deterministic embedded database for constrained systems and microcontrollers. KV, time-series, and fixed-schema relational tables behind one C99 API. | C99 |
| [loxdb_pro_docs](https://github.com/Vanderhell/loxdb_pro_docs) | Public API-level documentation for the commercial `loxdb_pro` module set. | Docs / C API contracts |
| [loxguard](https://github.com/Vanderhell/loxguard) | Embedded C guard-runtime for supervised execution boundaries, failure events, policy decisions, and blackbox evidence. | C99 |
| [micro-toolkit](https://github.com/Vanderhell/micro-toolkit) | Collection of small composable embedded C99 libraries. | C99 |
| [embedded-guard libraries](#embedded-guard--safety-monitoring--recovery) | Health, watchdog, boot, panic, OTA, and flash support libraries. | C99 |
| [IOBusMonitor](https://github.com/Vanderhell/IOBusMonitor) | Multi-protocol desktop tool for Modbus TCP/RTU and Siemens S7 PLCs. | C# |
| [RTULogSuite](https://github.com/Vanderhell/RTULogSuite) | Modbus RTU logging toolchain: ESP32 firmware + Windows visualization app. | C++ / C# |
| [iotspool](https://github.com/Vanderhell/iotspool) | Persistent store-and-forward MQTT queue for embedded systems. | C99 |

---

## 🔧 micro-toolkit — Modular C99 libraries for embedded systems

A collection of composable libraries sharing the same philosophy:

> no heap, no dependencies, no code generation — just `#include` and go.

### Toolkit modules

- [`microsh`](https://github.com/Vanderhell/microsh) — debug shell with history and tab completion.
- [`microlog`](https://github.com/Vanderhell/microlog) — multi-backend structured logging.
- [`microfsm`](https://github.com/Vanderhell/microfsm) — table-driven finite state machine engine.
- [`microres`](https://github.com/Vanderhell/microres) — retry with backoff, circuit breaker, and rate limiter.
- [`microconf`](https://github.com/Vanderhell/microconf) — schema-driven config with CRC and flash storage.
- [`microcbor`](https://github.com/Vanderhell/microcbor) — minimal CBOR encoder/decoder.
- [`micoring`](https://github.com/Vanderhell/micoring) — generic lock-free SPSC ring buffer.
- [`microtimer`](https://github.com/Vanderhell/microtimer) — software timer manager for one-shot and periodic timers.
- [`microbus`](https://github.com/Vanderhell/microbus) — topic-based event/pub-sub bus.
- [`iotspool`](https://github.com/Vanderhell/iotspool) — persistent MQTT store-and-forward queue.

---

## 🔗 embedded-guard — Safety, monitoring & recovery

Libraries that bridge embedded diagnostics, monitoring, recovery, and firmware lifecycle.

- [`microhealth`](https://github.com/Vanderhell/microhealth) — runtime health monitor with metrics and threshold-based alerts.
- [`microwdt`](https://github.com/Vanderhell/microwdt) — per-task software watchdog with escalation states.
- [`microboot`](https://github.com/Vanderhell/microboot) — boot and recovery manager with crash-loop detection.
- [`microassert`](https://github.com/Vanderhell/microassert) — unified panic system with hook chain and severity levels.
- [`microota`](https://github.com/Vanderhell/microota) — OTA update flow with chunking, CRC, version checks, commit/rollback.
- [`microflash`](https://github.com/Vanderhell/microflash) — unified flash abstraction for NOR/EEPROM/FRAM/RAM-like storage.

---

## 🛡️ Bare-metal safety & diagnostics

Small utilities for writing safer and more debuggable embedded C.

- [`panicdump`](https://github.com/Vanderhell/panicdump) — crash dump library for Cortex-M3/M4: capture on fault, survive reboot, decode offline.
- [`MCU-Malloc-Tracker`](https://github.com/Vanderhell/MCU-Malloc-Tracker) — deterministic heap diagnostics for bare-metal MCUs.
- [`nvlog`](https://github.com/Vanderhell/nvlog) — power-loss safe append log for FRAM/EEPROM/NOR flash.
- [`defer`](https://github.com/Vanderhell/defer) — automatic resource cleanup for C via `DEFER()` macro.
- [`cguard`](https://github.com/Vanderhell/cguard) — scope guards and result types for C.
- [`safemath`](https://github.com/Vanderhell/safemath) — overflow-checked arithmetic and buffer sizing helpers.
- [`microcrypt`](https://github.com/Vanderhell/microcrypt) — SHA-256, HMAC-SHA256, AES-128 ECB/CBC.
- [`microdh`](https://github.com/Vanderhell/microdh) — minimal X25519 key exchange for embedded systems.
- [`microtest`](https://github.com/Vanderhell/microtest) — single-header C test framework.

---

## 📦 Binary formats & data engines

- [`num8`](https://github.com/Vanderhell/num8) — O(1) membership engine for 8-digit numbers using a fixed bitset.
- [`IronFamily.FileEngine`](https://github.com/Vanderhell/IronFamily.FileEngine) — binary IoT file engines: config, structured logs, and firmware update package formats.

---

## 🏭 Industrial IoT & protocols

Desktop tools and firmware for real-world industrial communication.

- [`IOBusMonitor`](https://github.com/Vanderhell/IOBusMonitor) — multi-protocol desktop tool for Modbus TCP/RTU and Siemens S7 PLCs.
- [`RTULogSuite`](https://github.com/Vanderhell/RTULogSuite) — complete Modbus RTU logging toolchain: ESP32 firmware + Windows visualization.
- [`iotspool`](https://github.com/Vanderhell/iotspool) — persistent store-and-forward MQTT queue.
- [`uMesh`](https://github.com/Vanderhell/uMesh) — lightweight mesh networking stack for ESP32 over raw 802.11.
- [`num8-lup`](https://github.com/Vanderhell/num8-lup) — low-bandwidth update propagation protocol for constrained links.

---

## 🖥️ Desktop & .NET

- [`MultiGpuHelper`](https://github.com/Vanderhell/MultiGpuHelper) — C# library for scheduling compute workloads across multiple GPUs.
- [`CrudFramework`](https://github.com/Vanderhell/CrudFramework) — lightweight CRUD framework for .NET, EF Core, SQLite/SQL Server, and WPF-ready bindings.

---

## ⚡ Hardware projects

- [`securebox-hw`](https://github.com/Vanderhell/securebox-hw) — secure hardware password manager concept on ESP32-S3 with external encrypted storage.
- [`Pragotron-Controller`](https://github.com/Vanderhell/Pragotron-Controller) — minute-impulse controller for a Pragotron stepper clock.

---

## Focus

I am interested in embedded reliability, deterministic storage, firmware diagnostics, industrial data systems, and practical AI-assisted engineering.

Most of my projects follow the same rule:

> small code, clear contracts, real tests, and no claims without evidence.
