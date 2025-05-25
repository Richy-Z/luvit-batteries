# `Richy-Z/base32`

[![Publish to Lit](https://github.com/Richy-Z/base32/actions/workflows/lit.yml/badge.svg)](https://github.com/Richy-Z/base32/actions/workflows/lit.yml)

A base32 implementation made in pure Lua which is fully compliant with [RFC 4648](https://datatracker.ietf.org/doc/html/rfc4648).

## Installation

You can install this little library using `lit`:

```sh
lit install Richy-Z/base32
```

## Using base32

Require the library and use one of two methods: `encode` or `decode`.

```lua
local base32 = require("base32")

local encoded = base32.encode("Numelon Ltd. <3 Luvit")
local decoded = base32.decode("NZ2W2ZLMN5XCAPBTEBWHK5TJOQ======")

assert(encoded == decoded)
```
