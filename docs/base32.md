# `Richy-Z/base32`

An [RFC 4648](https://datatracker.ietf.org/doc/html/rfc4648)-compliant Base32 encoder/decoder in pure Lua.

Fully strips whitespace and padding on decode, and emits padding during encoding for standard compliance.

##  Usage

```lua
local base32 = require("base32")
```

---

### `base32.encode(str)`

Encodes a string into Base32 according to [RFC 4648](https://datatracker.ietf.org/doc/html/rfc4648).

- Padding with `=` is always added, as per the specification.
- Case is always uppercased.
- Output is a plain string.

```lua
print(base32.encode("foobar")) -- MZXW6YTBOI======

assert(encode("foobar") == "MZXW6YTBOI======")
```

###  `base32.decode(str)`

Decodes a Base32 string into its original content.

- Whitespace and padding are stripped automatically from the input string.
- Returns `nil, errorStr` if invalid Base32 characters are encountered.

```lua
print(base32.decode("MZXW6YTBOI======")) -- foobar

print(base32.decode("MZXW6 YT B O I======")) -- foobar

assert(decode("M  ZX W6Y    TBOI======") == "foobar")

local ok, err = base32.decode("??")
assert(not ok)
print(err) -- Invalid base32 character: ?
```
