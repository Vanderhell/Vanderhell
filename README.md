## Hi, I'm Vanderhell 👋 [![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/U4Q721ZX4J)

I build industrial software, embedded firmware tools, and small deterministic engines for systems that have to keep working when conditions are not ideal.

My work focuses on practical **C99**, **C#**, and **C++** tooling for:

- embedded firmware
- industrial software and communication
- diagnostics and reliability
- storage and power-loss recovery
- data acquisition
- constrained edge systems

> Build tools that are small enough to understand, strict enough to trust, and useful outside of demos.

My usual design bias:

- deterministic behavior
- clear contracts and failure modes
- small integration surfaces
- zero or minimal dependencies
- caller-owned state where possible
- bounded memory and execution where practical
- tests before claims

🌐 **Project documentation:** [vanderhell.github.io](https://vanderhell.github.io)

---

## LOX — Liquid Oxygen

**LOX** is the technical brand for my embedded and systems projects. The name represents concentrated engineering: compact code, high pressure, predictable behavior, and systems that can be tested instead of guessed.

The LOX family consists of focused libraries rather than one large framework:

- [`loxdb`](https://github.com/Vanderhell/loxdb) — deterministic embedded database for constrained systems and microcontrollers
- [`loxdb_pro_docs`](https://github.com/Vanderhell/loxdb_pro_docs) — public API documentation for the commercial `loxdb_pro` modules
- [`loxdust`](https://github.com/Vanderhell/loxdust) — verified persistent object storage with recovery operations
- [`loxbudget`](https://github.com/Vanderhell/loxbudget) — heap-free admission control based on resource budgets
- [`loxboot`](https://github.com/Vanderhell/loxboot) — zero-heap bootloader core with A/B slots and rollback-oriented flow
- [`loxguard`](https://github.com/Vanderhell/loxguard) — supervised execution boundaries and failure evidence
- [`loxalarm`](https://github.com/Vanderhell/loxalarm) — deterministic alarm-state core
- [`loxseq`](https://github.com/Vanderhell/loxseq) — power-loss-aware step sequencer
- [`loxperm`](https://github.com/Vanderhell/loxperm) — permissive and interlock evaluator
- [`loxsort`](https://github.com/Vanderhell/loxsort) — constraint-aware deterministic sorting
- [`loxc`](https://github.com/Vanderhell/loxc) — trainable codec for domain-specific text payloads

---

## Embedded C99 projects

- [`axiom-one`](https://github.com/Vanderhell/axiom-one) — focused deterministic primitives for common embedded problems
- [`micro-toolkit`](https://github.com/Vanderhell/micro-toolkit) — collection of small, composable embedded C99 libraries
- [`micronet`](https://github.com/Vanderhell/micronet) — LAN-first messaging for embedded nodes and desktop diagnostics
- [`uMesh`](https://github.com/Vanderhell/uMesh) — lightweight ESP32 mesh networking over raw 802.11
- [`iotspool`](https://github.com/Vanderhell/iotspool) — persistent store-and-forward MQTT queue

### Micro toolkit

- [`microsh`](https://github.com/Vanderhell/microsh) — debug shell with history and tab completion
- [`microlog`](https://github.com/Vanderhell/microlog) — multi-backend structured logging
- [`microfsm`](https://github.com/Vanderhell/microfsm) — table-driven finite-state machine engine
- [`microres`](https://github.com/Vanderhell/microres) — retry, backoff, circuit breaker, and rate limiter
- [`microconf`](https://github.com/Vanderhell/microconf) — schema-driven configuration with CRC and flash storage
- [`microcbor`](https://github.com/Vanderhell/microcbor) — minimal CBOR encoder and decoder
- [`micoring`](https://github.com/Vanderhell/micoring) — lock-free SPSC ring buffer
- [`microtimer`](https://github.com/Vanderhell/microtimer) — one-shot and periodic software timers
- [`microbus`](https://github.com/Vanderhell/microbus) — topic-based event and publish/subscribe bus

### Safety, monitoring, and recovery

- [`microhealth`](https://github.com/Vanderhell/microhealth) — runtime health monitoring
- [`microwdt`](https://github.com/Vanderhell/microwdt) — per-task software watchdog
- [`microboot`](https://github.com/Vanderhell/microboot) — boot and crash-loop recovery manager
- [`microassert`](https://github.com/Vanderhell/microassert) — unified panic system
- [`microota`](https://github.com/Vanderhell/microota) — OTA update flow with commit and rollback
- [`microflash`](https://github.com/Vanderhell/microflash) — unified flash abstraction
- [`panicdump`](https://github.com/Vanderhell/panicdump) — persistent Cortex-M3/M4 crash dumps
- [`MCU-Malloc-Tracker`](https://github.com/Vanderhell/MCU-Malloc-Tracker) — deterministic heap diagnostics for bare-metal MCUs
- [`nvlog`](https://github.com/Vanderhell/nvlog) — power-loss-safe append log
- [`microtest`](https://github.com/Vanderhell/microtest) — single-header C test framework

### Safer embedded C and cryptography

- [`defer`](https://github.com/Vanderhell/defer) — automatic resource cleanup through `DEFER()`
- [`cguard`](https://github.com/Vanderhell/cguard) — scope guards and result types for C
- [`safemath`](https://github.com/Vanderhell/safemath) — checked arithmetic and buffer sizing
- [`microcrypt`](https://github.com/Vanderhell/microcrypt) — SHA-256, HMAC-SHA256, and AES-128 ECB/CBC/GCM
- [`microdh`](https://github.com/Vanderhell/microdh) — minimal X25519 key exchange

---

## Industrial, data, and desktop projects

### Industrial communication and IoT

- [`IOBusMonitor`](https://github.com/Vanderhell/IOBusMonitor) — desktop tool for Modbus TCP/RTU and Siemens S7 PLCs
- [`RTULogSuite`](https://github.com/Vanderhell/RTULogSuite) — ESP32 and Windows Modbus RTU logging toolchain
- [`Pragotron-Controller`](https://github.com/Vanderhell/Pragotron-Controller) — minute-impulse controller for a Pragotron stepper clock

### Data and file engines

- [`num8`](https://github.com/Vanderhell/num8) — O(1) membership engine for eight-digit numbers
- [`num8-lup`](https://github.com/Vanderhell/num8-lup) — low-bandwidth update propagation protocol
- [`IronFamily.FileEngine`](https://github.com/Vanderhell/IronFamily.FileEngine) — binary IoT file engines and tooling

### .NET

- [`MultiGpuHelper`](https://github.com/Vanderhell/MultiGpuHelper) — scheduling compute workloads across multiple GPUs
- [`CrudFramework`](https://github.com/Vanderhell/CrudFramework) — lightweight CRUD framework for .NET applications

### Hardware

- [`securebox-hw`](https://github.com/Vanderhell/securebox-hw) — secure hardware password manager concept

---

## Collaboration

I welcome practical feedback from people working with embedded C, microcontrollers, RTOS or bare-metal firmware, industrial devices, and constrained edge systems.

Useful contributions include:

- integration on real hardware
- failure reports with logs and reproducible evidence
- storage and power-loss validation
- portability feedback
- code and API review
- documentation and example improvements

