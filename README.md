# ❤️ Luvit Batteries

> Batteries included!

[![Publish to Lit](https://github.com/Richy-Z/base32/actions/workflows/lit.yml/badge.svg)](https://github.com/Richy-Z/base32/actions/workflows/lit.yml)

This repository is a growing collection of Lua libraries I've developed over the years while building with [Luvit](https://luvit.io). These libraries have remained internal to the Numelon ecosystem for a long time - but I'm now beginning to open-source the more foundational and reusable ones.

It's hard to overstate how powerful and enjoyable Luvit has been in my development journey. Since around 2020/2021, it has served as the backbone of nearly all Numelon software. After about a year of using it, we committed fully and gradually rewrote everything around Luvit. It now powers high-complexity, production-critical platforms such as [Rubiš](https://rubis.app) (a full-featured pasting service, CDN, and more), and the Numelon Stock Exchange, which involves high-throughput, real-time infrastructure - along with various internal services, bots, and image pipelines.

While Luvit itself is *tremendous*, its ecosystem lacks well-maintained libraries on Lit. Yes, you can use LuaRocks libraries and pure Lua libraries (as expected), but ideally Luvit's Lit should be just *amazing*.

## Libraries

These libraries are available as standalone Luvit-compatible packages via [Lit](https://luvit.io/lit.html):

| Package              | Description                           | Install Command                       | Documentation |
|----------------------|---------------------------------------|----------------------------------------|-|
| `Richy-Z/base32`     | RFC 4648-compliant Base32 implementation in pure Lua | `lit install Richy-Z/base32`| [Here](./docs/base32.md) |
| `Richy-Z/clock`     | Precise UNIX time util with ISO 8601 support, millisecond precision, and UTC-safe parsing | `lit install Richy-Z/clock` | [Here](./docs/clock.md) |
| `Richy-Z/string-extensions` | Small extensions to Lua's default string library | `lit install Richy-Z/string-extensions` | [Here](./docs/string-extensions.md) |

---

More libraries from both the Numelon stack and my personal projects will be released over time.
