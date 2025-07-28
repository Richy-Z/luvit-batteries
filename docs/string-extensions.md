# `Richy-Z/string-extensions`

A set of lightweight extensions to Lua's default string library. These functions are injected directly into the global string table to feel like native utilities to make string manipulation more convenient, expressive, and readable.

## Usage

```lua
require("string-extensions")
-- all functions are now available as part of the global string table
```

Previously, the library had to be "activated" by requiring and then running the function it returned like this: `require("string-extensions")()`. This is no longer required, however the module still returns an empty function to maintain compatibility with legacy scripts that still rely on running it.

---

###  `string.startswith(str, prefix)`

Returns `true` if `str` starts with `prefix`.

```lua
print(string.startswith("hello world", "hel")) -- true
```

### `string.endswith(str, suffix)`

Returns `true` if `str` ends with `suffix`.

```lua
print(string.endswith("hello.lua", ".lua")) -- true
```

###  `string.trim(str)`

Strips leading and trailing whitespace from a string.

```lua
print(string.trim("   padded string   ")) -- "padded string"
```

###  `string.zfill(str, width)`

Pads the string on the left with zeroes (`0`) until it reaches the specified width.

If the string is already at least `width` characters long, it is returned unchanged.

```lua
print(string.zfill("42", 5)) -- "00042"
print(string.zfill("hello", 3)) -- "hello" -- not padded because it is already >= 3 chars
```

### `string.split(str, separator?)`

Splits a string by a pattern-based separator (defaults to `%s`, i.e. any whitespace).

> [!WARNING]
> If the seeparator contains multiple characters, e.g. `.,`, then each character is treated as a **completely separate** delimiter. This is because the separator is treated as a Lua pattern.
>
> Please also check [`string.splitphrase`](#stringsplitphrasestr-separator) to ensure you are using the correct split for your use case. I made a huge mistake with `string.split` once, which caused me to make `string.splitphrase`.

```lua
p(string.split("Hi.Bob,And.3.,44", ".,"))
-- { "Hi", "Bob", "And", "3", "44" }
-- . and , were treated as two separate delimiters
```

###  `string.splitphrase(str, separator?)`

Splits a string by a literal separator (defaults to whitespace). Unlike `string.split`, the full string you provide is treated as the exact separator - not a pattern and not a set of characters.

```lua
p(string.splitphrase("Hi.Bob,And.3.,44", ".,"))
-- { "Hi.Bob,And.3", "44" }
-- ., was treated as a literal separator
-- unlike string.split(),  The string was now only separated at the end,
-- where ., were present together in the exact order.
```

### `string.wrap(str, limit?)`

Wraps long strings at a given character limit (default: `80`) whilst also ensuring that words aren't broken across lines.

```lua
print(string.wrap("This sentence is being wrapped after 20 characters", 20))
--[[
This sentence is
being wrapped after
20 characters
]]
```

### `string.deregexify(str)`

Escapes all Lua pattern characters in a string so it can be safely used in `string.match`, `string.gsub`, etc. without being interpreted as actual pattern characters.

```lua
local escaped = string.deregexify("1+1=2?")
print(escaped) -- "1%+1=2%?"
```

###  `string.random(length, charset?)`

Generates a random string that is `length` characters long, using the given charset (or alphanumerics by default, if `charset` is omitted.)

```lua
print(string.random(10)) -- e.g. "aZ7qT19BcP"

print(string.random(5, "abc")) -- e.g. "abacb"
```
