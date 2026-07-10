# Systems & Architecture — From Theory to Implementation

A 43-chapter technical book on system design, software architecture, and systems programming, written entirely as a single self-contained HTML artifact — dark terminal theme, syntax-highlighted C++ and Rust throughout, sidebar navigation, no build step required.

**[→ Open the book](./system-design-book.html)**

---

## What this is

Most system design material forces a choice between two failure modes: theory dense enough to explain *why* a decision matters but too abstract to ever build, or code dense enough to copy-paste but silent on the reasoning that would let you reuse the decision somewhere else. This book was built to close that gap for one specific reader — someone who already writes C++ and Rust and wanted a single, continuous resource that never separates the two.

Every chapter follows the same fixed structure:

```
theory  →  trade-offs  →  C++ implementation  →  Rust implementation  →  what each language forces you to confront
```

That last step is the part most resources skip. It's not "here are two code samples that do the same thing" — it's a deliberate comparison of what each language's compiler catches automatically versus what it leaves to programmer discipline, repeated at every layer from a single class to a distributed operating system.

## Structure

The book is split into two volumes, seven and five parts respectively, 43 chapters total.

### Volume I — Foundations → Systems (Chapters 1–31)

| Part | Chapters | Subject |
|---|---|---|
| I — Foundations | 1–4 | What system design actually is, computational cost models, memory (stack/heap/ownership), concurrency primitives |
| II — Design Principles | 5–9 | SOLID reconsidered, creational/structural/behavioral patterns, Layered/Hexagonal/Clean Architecture |
| III — Distributed Systems Fundamentals | 10–13 | CAP theorem, Raft consensus, replication & partitioning, event-driven messaging |
| IV — Building Blocks | 14–18 | Load balancing, caching, databases (SQL/NoSQL), queues & streaming, API design |
| V — Case Studies | 19–23 | URL shortener, rate limiter, chat system, news feed, distributed file storage |
| VI — Advanced Topics | 24–28 | Microservices vs. monoliths, service mesh, observability, security, performance engineering |
| VII — Systems Programming Capstones | 29–31 | C++ (RAII/move semantics), Rust (lifetimes/async/unsafe), a toy distributed KV store |

### Volume II — Applied Systems (Chapters 32–43)

| Part | Chapters | Subject |
|---|---|---|
| VIII — Specialized Storage & Data Systems | 32–34 | B-trees & LSM-trees, search & inverted indices, time-series storage |
| IX — Parallel and Hardware-Aware Computing | 35–37 | Lock-free data structures, SIMD & data-oriented design, GPU computing |
| X — Peer-to-Peer and Decentralized Systems | 38–40 | DHTs & Kademlia, blockchain & Byzantine fault tolerance, WebAssembly |
| XI — Operating Systems and Low-Level Runtime | 41–42 | Microkernels & capability-based security, compiler & language runtime internals |
| XII — Volume II Capstone | 43 | A peer-to-peer file-sharing protocol |

## Why it's one HTML file

No build step, no dependency installation, no server. Open it in a browser and it works — sidebar navigation, syntax highlighting, and progress tracking are all implemented in vanilla HTML/CSS/JS with zero external requests. This was a deliberate choice: a book about removing unnecessary complexity from systems shouldn't itself require a toolchain to read.

## The five ideas underneath all 43 chapters

The book's actual argument isn't the 43 topics — it's that a small number of ideas do almost all the real work, reappearing under different names at every scale. They're named explicitly in the closing sections of Chapter 31 and Chapter 43, and threaded through every chapter in between:

1. **The Dependency Rule** (Ch. 9) — depend on abstractions, never on concrete infrastructure. Appears as Chapter 1's logger interface, Chapter 5's payment gateway, Chapter 24's saga steps, Chapter 41's OS capabilities, and Chapter 43's DHT routing.
2. **No axis improves for free** (Ch. 2) — every cache, index, replica, or optimization buys one property by spending another. Appears in caching, indexing, replication vs. erasure coding, B-trees vs. LSM-trees, and generational garbage collection.
3. **Compiler-enforced vs. discipline-enforced** (Ch. 3–4) — the recurring C++/Rust comparison was never about which language is "better," but about where each language draws the line between what the compiler verifies and what a human must remember. Reappears in ownership, concurrency, WASM sandboxing, and OS-level capabilities.
4. **Per-data-type discipline, not per-system** (Ch. 10) — consistency, schema strictness, and caching policy are never one global choice for an entire system; each piece of data gets its own answer based on its own requirements.
5. **The speculative-generality test** (Ch. 5) — before adding an abstraction, a service boundary, or a consensus protocol: can you name the second implementation, the measured bottleneck, or the concrete organizational reason? Reapplied at every layer, up to and including whether blockchain is the right tool at all (Ch. 39).

## Format conventions

- **Code windows** are labeled with a filename and rendered in a dark, monospace terminal style. Every code sample is a real, runnable shape of the idea being discussed — not pseudocode — with inline comments doing the actual teaching.
- **Callout boxes** (amber left border) mark a single, load-bearing insight per section — the sentence worth remembering if nothing else from that section sticks.
- **"What to carry forward"** closes every chapter with 2–3 bullets connecting that chapter's content forward and backward to the rest of the book, rather than summarizing what was just read.
- Simplified or "toy" implementations are labeled honestly, in-line, with a note on exactly what a production version would add — this convention starts in Chapter 11 and holds for the rest of the book.

## How to use it

- **Sequentially**, front to back, if you're working through it as a course.
- **By part**, if you already know a topic and want the specific chapter's C++/Rust comparison or worked example.
- **By cross-reference** — nearly every chapter cites at least one earlier chapter by number and section (e.g., "Chapter 12, §12.5's consistent-hash ring"). Following those citations is usually more useful than reading linearly once you're past Part I, since the same handful of ideas keep resurfacing in unfamiliar contexts.

## Status

Complete — 43/43 chapters, both volumes. Built iteratively, one chapter per working session, each one checked against everything written before it for consistency of terminology, cross-references, and the C++/Rust comparison format.

## License / usage

Personal reference material. No license asserted — reuse, adapt, or extend freely.
