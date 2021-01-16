<h1 align=center>wires.lua 🔌</h1>
<h3 align=center>An assortment of useful string functions ⚡</h3>


# Installation

## Luarocks

If you are using [luarocks](https://luarocks.org), just run:

```
luarocks install wires
```

## Manual

Copy the [wires.lua](wires.lua) file somewhere where your Lua interpreter will be able to find it and require it accordingly:

```lua
local wires = require("wires")
```

## Tips

You can extend the Lua string namespace by doing:
```lua
for k, v in pairs(wires) do 
    string[k] = v 
end
```

so you can use them as string methods:
```lua
(""):trim()
```
or
```lua
string.trim("")
```

## Interface

`wire.starts(s, prefix)` Find if string `s` starts with `prefix`

```lua
wire.starts("foo bar baz", "foo") -> true
```

Arguments:

* `s` `(string)` - String to match
* `prefix` `(string)` - String to match in `s`

Returns:

* `(boolean)` - `true` if `s` starts with `prefix`, `false` if not

---
`wire.ends(s, suffix)` Find if string `s` ends with `suffix`

```lua
wire.ends("foo bar baz", "baz") -> true
```

Arguments:

* `s` `(string)` - String to match
* `suffix` `(string)` - String to match in `s`

Returns:

* `(boolean)` - `true` if `s` ends with `suffix`, `false` if not

---
`wire.trim(s)` Remove whitespace (defined as Lua pattern `"%s"`) from the beginning and end of a string

```lua
wire.trim(" foo ") -> "foo"
```

Arguments:

* `s` `(string)` - String to trim

Returns:

* `(string)` - The trimmed string

---
`wires.escape(s[, mode])` Escape magic characters of `s` so that it can be used as a pattern. The optional argument mode may be `"*i"` (for case insensitive)

```lua
wires.escape("%s", "*i") -> "%%[sS]"
```

Arguments:

* `s` `(string)` - String to escape
* `mode` `(string)` - String for whether the escape should be case insensetive

Returns:

* `(string)` - The escaped string

---
`wires.gsplit(s, sep[, start[, plain]]) -> iter() -> e[, captures...]` Split `s` by a separator pattern (or plain string) and iterate over the elements

```lua
for c in wires.gsplit('foo bar baz', '%s') do
   print(c)
end
```

Arguments:

* `s` `(string)` - string to gsplit
* `sep` `(string)` - pattern to gsplit `s`
* `start` `(number)` - Capture to begin at
* `plain` `(boolean)` - Whether to match patterns or not

Returns:

* `c` `(string)` - A capture from `s`

---
`wires.lines(s[, opt]) -> iter() -> s` Iterate the lines of a string, The lines are split at `\r\n`, `\r` and `\n` markers

```lua
for c in wires.lines("foo\nbar\nbaz") do
    print(c)
end
```

Arguments:

* `s` `(string)` - String with lines to iterate over
* `opt` `(string)` - `*L` (include line endings; default) or `*l` (exclude).

Returns:

* `c` `(string)` - The captured line

---
`wires.tohex(s, upper)` Convert a hex string to its binary representation

```lua
wires.tohex("foo") -> "666f6f"
```

Arguments:

* `s` `(string)` - String to convert to it's hex representation
* `upper` `(boolean)` - Whether alphabetical characters should be capitalised

Returns:

* `(string)` - Hex representation of `s`

---
`wires.fromhex(s)` Convert a hex string to its binary representation

```lua
wires.fromhex("666f6f") -> "foo"
```

Arguments:

* `s` `(string)` - Hex string to convert to it's binary represenation

Returns:

* `(string)` - Binary representation of `s`

---
# License

This library is free software; You may redistribute and/or modify it under the terms of the MIT license. See [LICENSE](LICENSE) for details.
