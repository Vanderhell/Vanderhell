## Hi, I'm Vanderhell 👋

I build industrial software, embedded firmware tools, and small deterministic engines for systems that have to keep working when conditions are not ideal.

**LOX** means **Liquid Oxygen** — the brand name I use for my embedded and systems projects. For me, it stands for concentrated engineering: compact code, high pressure, clear contracts, and behavior that can be tested instead of guessed.

My work is focused on practical C/C#/C++ tooling for production, diagnostics, firmware reliability, industrial communication, data acquisition, and edge systems. The common thread is simple: build tools that are small enough to understand, strict enough to trust, and useful outside of demos.

My usual design bias:

- deterministic behavior
- small integration surface
- clear failure modes
- zero or minimal dependencies
- caller-owned state where possible
- tests before claims
- real-world tooling over showcase code

---

## Collaboration

I am looking for people who can test, break, review, and validate embedded C projects on real hardware.

Useful feedback areas:

- embedded C testing
- MCU and board-level validation
- storage and power-loss testing
- reliability and diagnostics
- industrial and edge use cases
- examples, integration feedback, and documentation review

If you work with firmware, MCU platforms, RTOS/bare-metal systems, industrial devices, or constrained edge systems, I am interested in practical feedback — especially reports that include hardware, configuration, failure cases, and test evidence.

---

## Main projects

### 🗄️ loxdb — Deterministic embedded database for MCU/edge systems

[`loxdb`](https://github.com/Vanderhell/loxdb) is a compact **C99 embedded database** for firmware, dataloggers, controllers, and small edge runtimes.

It is built for cases where a full SQL database is too heavy, but raw files, ad-hoc structs, or fragile flash layouts are not enough.

`loxdb` combines three storage models behind one API surface:

- **KV storage** for configuration, cache entries, and TTL-backed state
- **Time-series storage** for sensor samples, counters, and rolling telemetry
- **Fixed-schema relational tables** for small indexed structured records

Core design:

- one allocation at `lox_init()`
- fixed RAM budgeting
- zero external dependencies
- RAM-only or storage-backed operation
- optional WAL-backed persistence and recovery
- embedded-first storage HAL
- predictable behavior under constrained memory

`loxdb` is not a tiny SQLite clone. SQLite is excellent, but it targets a different operating point. `loxdb` is intentionally narrower: deterministic storage for constrained firmware where predictable memory, small API surface, and recoverable writes matter more than SQL features.

**License:** MIT open-source core.  
**Commercial extension:** [`loxdb_pro_docs`](https://github.com/Vanderhell/loxdb_pro_docs) contains public API-level documentation for the planned/commercial PRO module set.

---

### 🧩 loxdb_pro — Commercial production modules around loxdb core

[`loxdb_pro_docs`](https://github.com/Vanderhell/loxdb_pro_docs) documents the public integration-facing API for the commercial `loxdb_pro` layer.

The PRO layer is intended for embedded products that need more than local storage. It adds the production-facing pieces around the core database: validation, integrity checks, policy gates, observability, migration, transport, recovery planning, and host tooling.

Planned/module areas include:

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

It introduces **Guard Blocks** and **Checked Guard Blocks**: explicit execution boundaries around risky firmware paths such as parsers, protocol handlers, optional modules, recovery-sensitive routines, and code that should never fail silently.

Instead of only failing with an assert or watchdog reset, `loxguard` turns unsafe execution states into structured runtime evidence:

- lifecycle events
- policy decisions
- blackbox records
- reports
- CSV/KV import-export paths
- optional persistence and ecosystem adapters

Current scope includes checked span/arena primitives, Guard Block lifecycle tracking, failure reporting, policy decisions, local blackbox evidence, and host-tested integration paths.

`loxguard` does not claim full memory safety for arbitrary C code and is not a safety-certified framework. Its value is narrower and practical: make risky execution paths easier to detect, record, inspect, and react to in small embedded C systems.

---

### 🚨 loxalarm — Deterministic alarm-state core for embedded firmware

[`loxalarm`](https://github.com/Vanderhell/loxalarm) is a small, heap-free **C99** alarm state-machine core for embedded firmware.

It models the lifecycle of one process alarm condition with behavior that is usually scattered across application code, HMI logic, PLC glue, or vendor-specific runtime layers.

It includes:

- on-delay and off-delay handling
- latching and acknowledge flow
- shelving for maintenance or temporary suppression
- reason flags and transition visibility
- snapshot/restore support for caller-owned persistence

`loxalarm` is designed for firmware that needs PLC-style alarm semantics without depending on a PLC vendor stack, HMI runtime, operating system, network protocol, or dynamic memory.

It is not a safety-certified alarm system, historian, HMI, or OPC UA/MQTT/Modbus binding. Its value is narrower: a deterministic runtime alarm object that higher-level firmware, diagnostics, logging, persistence, or UI layers can consume.

**License:** MIT.

---

### 🔁 loxseq — Power-loss-aware step sequencer for embedded C firmware

[`loxseq`](https://github.com/Vanderhell/loxseq) is a small, heap-free **C99** step sequencer for firmware workflows that must survive reset, brownout, watchdog recovery, or power loss.

It checkpoints step progress to caller-provided storage and computes a recovery verdict on reboot, so firmware does not have to blindly restart a physical process from the beginning.

Core ideas:

- CRC-protected persistent checkpoint record
- per-step resume policy
- conservative recovery downgrades
- tick-driven execution using caller-provided `now_ms`
- caller-owned state
- no heap, globals, or floating point
- optional branching via `loxseq_set_next_step` and `LOXSEQ_STEP_BRANCH`

Typical use cases include fill/heat/drain sequences, calibration flows, provisioning, controlled shutdown/startup flows, and multi-step maintenance procedures.

`loxseq` is not an RTOS scheduler, workflow language, database, or general task engine. Its value is narrower: deterministic step execution with explicit reboot recovery semantics.

**License:** MIT.

---

### 🔐 loxperm — Permissive / interlock evaluator for embedded firmware

[`loxperm`](https://github.com/Vanderhell/loxperm) is a small, heap-free **C99** single-header library for evaluating permissives and interlocks.

It gives firmware a deterministic answer to a simple but important question: **is this action allowed to start, and is it still allowed to continue?**

Core features:

- explainable deny mask
- first-out detection
- qualifier times for conditions that must remain true for a duration
- optional latching
- maintenance bypass support
- caller-owned state
- no heap, no floating point, and no hidden mutable runtime state

Typical use cases include pump starts, valve movement, actuator enable gates, machine interlocks, maintenance overrides, and process-control diagnostics where the firmware must explain exactly why an operation is blocked.

`loxperm` is not a safety-certified interlock system or PLC replacement. Its value is narrower: deterministic, explainable permission logic for embedded C firmware.

**License:** MIT.

---

### 🧬 loxc — Trainable C99 text codec for domain-specific payloads

[`loxc`](https://github.com/Vanderhell/loxc) is an experimental trainable text codec written in **C99**.

It is designed for cases where the developer already knows the shape of the transmitted or stored text: MQTT payloads, telemetry messages, logs, JSON-like records, protocol text, or repetitive domain-specific data.

Instead of trying to be a universal compressor, `loxc` lets you train a codec table from representative sample data, export that table, transfer it, and load it later in an application, tool, or embedded runtime.

Core ideas:

- frequency-based symbol selection
- matrix-based symbol layout
- nested submatrices for less frequent data
- binary encoded output
- trained lookup tables
- predictable table-driven decoding
- small C99 integration surface

`loxc` is not intended to compete with `gzip`, `zstd`, `brotli`, or `lz4`. Those are mature general-purpose compression systems.

The value of `loxc` is narrower: provide a small trainable codec option for developers who know their data and want a compact table-driven encoding path for specific text payloads.

It is not encryption and not a universal archive format.

---

### ⏱️ loxbudget — Deterministic admission control for embedded operations

[`loxbudget`](https://github.com/Vanderhell/loxbudget) is a small, heap-free **C99** library that decides whether an embedded operation should run — and at what level — based on configurable resource budgets, rate windows, and optional calibration.

It works as a deterministic pre-flight gate in front of risky firmware work: MQTT publish, OTA update, flash write, log burst, debug dump, parser invocation, queue allocation, or any operation that must be degraded, delayed, rejected, or allowed under pressure.

Core design:

- deterministic `check / enter / leave` decisions per operation profile
- no heap, no floats, no global mutable state
- caller-owned storage
- optional audit ring buffer for recent decisions
- optional rate windows and lifetime limits
- optional calibration and diagnostic strings
- single-header amalgamated distribution option
- stable public API starting at `v1.0.0` (semver)

Typical use cases:

- prevent MQTT storms from exhausting queue slots
- block OTA when voltage or flash budget is unsafe
- degrade logging under memory pressure
- reject non-critical work during survival mode
- enforce flash-write lifetime budgets

`loxbudget` is not a scheduler, allocator, watchdog, logger, profiler, or RTOS replacement. Its value is narrower: an admission-control layer that gives firmware a deterministic answer to "may this operation run right now, and how?".

**License:** MIT.

---

## Project map

| Project | Description | Tech |
|---|---|---|
| [loxdb](https://github.com/Vanderhell/loxdb) | Deterministic embedded database for constrained systems and microcontrollers. KV, time-series, and fixed-schema relational tables behind one C99 API. | C99 |
| [loxdb_pro_docs](https://github.com/Vanderhell/loxdb_pro_docs) | Public API-level documentation for the commercial `loxdb_pro` module set. | Docs / C API contracts |
| [loxguard](https://github.com/Vanderhell/loxguard) | Embedded C guard-runtime for supervised execution boundaries, failure events, policy decisions, and blackbox evidence. | C99 |
| [loxalarm](https://github.com/Vanderhell/loxalarm) | Deterministic alarm-state core for embedded firmware. Handles on/off delays, latching, acknowledge flow, shelving, reason flags, and snapshot/restore support. | C99 |
| [loxseq](https://github.com/Vanderhell/loxseq) | Power-loss-aware step sequencer for embedded firmware. Provides checkpointed step progress and reboot recovery/resume policy per step. | C99 |
| [loxperm](https://github.com/Vanderhell/loxperm) | Heap-free permissive/interlock evaluator with explainable deny mask, first-out detection, qualifier times, latching, and maintenance bypass. | C99 |
| [loxc](https://github.com/Vanderhell/loxc) | Experimental trainable C99 text codec for domain-specific payloads using trained lookup tables, matrix-based symbol layout, nested submatrices, and binary encoded output. | C99 |
| [loxbudget](https://github.com/Vanderhell/loxbudget) | Deterministic, heap-free admission-control library for embedded firmware. Pre-flight gate for risky operations based on resource budgets, rate windows, and calibration. | C99 |
| [micro-toolkit](https://github.com/Vanderhell/micro-toolkit) | Collection of small composable embedded C99 libraries. | C99 |
| [embedded-guard libraries](#embedded-guard--safety-monitoring--recovery) | Health, watchdog, boot, panic, OTA, and flash support libraries. | C99 |
| [IOBusMonitor](https://github.com/Vanderhell/IOBusMonitor) | Multi-protocol desktop tool for Modbus TCP/RTU and Siemens S7 PLCs. | C# |
| [RTULogSuite](https://github.com/Vanderhell/RTULogSuite) | Modbus RTU logging toolchain: ESP32 firmware + Windows visualization app. | C++ / C# |
| [iotspool](https://github.com/Vanderhell/iotspool) | Persistent store-and-forward MQTT queue for embedded systems. | C99 |

---

## 🔧 micro-toolkit — Modular C99 libraries for embedded systems

A collection of composable embedded libraries sharing the same philosophy:

> no heap, no dependencies, no code generation — just `#include` and go.

Toolkit modules:

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
