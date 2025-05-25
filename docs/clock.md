# `Richy-Z/clock`

A lightweight but precise clock utility library for [Luvit](https://luvit.io), with full support for:

- Nanosecond-precision UNIX time using `ffi`
- Millisecond resolution
- [ISO 8601 / RFC 3339](https://datatracker.ietf.org/doc/html/rfc3339) time formatting
- UTC-safe ISO 8601 string parsing
- Optional alias: `clock.now()` is equal to `clock.epoch()`

##  Usage

```lua
local clock = require("clock")
```

---

### `clock.epoch()`

- Alias: `clock.now()`

Returns the current UNIX time in seconds with fractional milliseconds using the OS’ native time function via FFI.

```lua
local currentTime = clock.epoch()

print(currentTime) -- 1748187427.5988
```

###  `clock.milliseconds()`

Uses `clock.epoch()` to give you the current UNIX time in milliseconds. It is a simple wrapper that just multiplies the result of `clock.epoch()` by 1000.

```lua
local currentMillis = clock.milliseconds()

print(currentMillis) -- 1748187535644
```

###  `clock.iso8601()`

Returns the current time in ISO 8601 format (UTC), including milliseconds (e.g., 2025-05-27T23:45:12.123Z).

```lua
local currentIso = clock.iso8601()

print(currentIso) -- '2025-05-25T15:40:20.902Z'
```

###  `clock.iso8601_parse(str)`

Parses `str`, hopefully an ISO 8601 formatted timestamp, back into a UNIX timestamp in seconds with fractional milliseconds (if present). Assumes UTC and accounts for local timezones automatically.

```lua
local example = "2025-05-27T23:45:12.123Z"
local parsed = clock.iso8601_parse(example)

print(parsed) -- 1748389512.123

assert(math.floor(iso8601_parse("2025-05-27T23:45:12.123Z")) == 1748389512)
```
