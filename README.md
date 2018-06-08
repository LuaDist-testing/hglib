# hglib

A pure-Lua library for interacting with Mercurial's command server. It's useful
for Lua applications that want to get all kinds of repository data fast.
Compared to the usual way of executing multiple `hg command`, this library
skips the overhead of starting up a new process every time.


## License

MIT.


## Usage

```
#!lua
local hglib = require 'hglib'
local client = hglib.Client.open('.')
local code, o, e, d = client:runcommand({'log', '-r0'})
client:close()
print('Output: ' .. o)
if #e > 0 then
	print('Error: ' .. e)
end
if #d > 0 then
	print('Debug: ' .. d)
end
```

See examples/ and spec/ for more.


## Caveats

lpc is Lua 5.1-only.


## Release Notes

### 0.8 (2016-10-25)

Initial release. Implemented methods include:

- `Client:connect()`
- `Client:open()`
- `Client:getencoding()`
- `Client:runcommand()`
- `Client:runcommand_co()`
- `Client:close()`


## TODO

### 2.0

- ORM-like interface from python-hglib

### 1.0

- Better docs
- Maybe use something better than lpc
- ??????
