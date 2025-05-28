# `Richy-Z/logger`

A lightweight per-instance logging utility for Luvit.

## Usage

Requiring the logger library returns a function which allows you to create a new logger instance.

```lua
local logger = require("logger")("debug", "!%Y-%m-%d %H:%M:%S", "./logs/my_log.log")
logger:info("Hi %d", os.time())
```

---

### `require("logger")(levelName, dateTimeFormat?, filePath?)`

Creates a new per-instance logger that prints formatted messages to both stdout and an optional log file.

- string `levelName`: Minimum log level to show. One of `"none"`, `"error"`, `"warning"`, `"info"`, or `"debug"`. Defaults to `"warning"` if invalid.
- string `dateTimeFormat`: An optional format string accepted by `os.date`, e.g. `""!%Y-%m-%d %H:%M:%S"` for UTC timestamps.
- string `filePath`: Optional path to a file where logs should also be written, without any of the ANSI colour codes / highlighting, etc.

This should return your new instance which will include the shortcut methods below:

```lua
logger:error(msg, ...)   -- level 1
logger:warning(msg, ...) -- level 2
logger:info(msg, ...)    -- level 3
logger:debug(msg, ...)   -- level 4
logger:p(msg, ...)       -- level 0, always logs (useful for prints)
```
