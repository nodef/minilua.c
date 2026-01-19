# MiniLua

This is Lua contained in a single header to be bundled in C/C++ applications with ease.
[Lua](https://www.lua.org/) is a powerful, efficient, lightweight, embeddable scripting language.
This library was created by [Eduardo Bart](https://github.com/edubart).

<br>

## Installation

Run:

```sh
$ npm i minilua.c
```

And then include `minilua.h` as follows:

```c
// main.c
#define MINILUA_IMPLEMENTATION  // or LUA_IMPL
#include <minilua.h>

int main() { /* ... */ }
```

Finally, compile while adding the path `node_modules/minilua.c` to your compiler's include paths.

```bash
$ clang -I./node_modules/minilua.c main.c  # or, use gcc
$ gcc   -I./node_modules/minilua.c main.c
```

You may also use a simpler approach with the [cpoach](https://www.npmjs.com/package/cpoach.sh) tool, which automatically adds the necessary include paths of all the installed dependencies for your project.

```bash
$ cpoach clang main.c  # or, use gcc
$ cpoach gcc   main.c
```

<br>

## Example Usage

```c
#define LUA_IMPL
#include <minilua.h>

int main() {
  lua_State *L = luaL_newstate();
  if(L == NULL)
    return -1;
  luaL_openlibs(L);
  luaL_loadstring(L, "print 'hello world'");
  lua_call(L, 0, 0);
  lua_close(L);
  return 0;
}
```

<br>

## Usage

Include `minilua.h` to use Lua API.
Then do the following in *one* C file to implement Lua:
```c
#define LUA_IMPL
#include <minilua.h>
```

By default it detects the system platform to use, however you can explicitly define one.

Note that almost no modification was made in the Lua implementation code,
thus there are some C variable names that may collide with your code,
therefore it is best to declare the Lua implementation in dedicated C file.

Optionally provide the following defines:
  - `LUA_MAKE_LUA`     - implement the Lua command line REPL

<br>

## Documentation

For documentation on how to use Lua read its [official manual](https://www.lua.org/manual/).

<br>

## Updates

- **25-Jul-2024**: Updated to Lua 5.4.7.
- **13-Nov-2023**: Updated to Lua 5.4.6.
- **28-Jan-2022**: Updated to Lua 5.4.4.
- **31-Mar-2021**: Updated to Lua 5.4.3.
- **03-Dec-2020**: Updated to Lua 5.4.2.
- **27-Nov-2020**: Library created, using Lua 5.4.2-rc1.

<br>

## Notes

This library tries to keep up with latest official Lua release.
The header is generated using the bash script `gen.sh` all modifications done is there.

<br>

## License

Same license as Lua, the MIT license, see LICENSE.txt for information.

<br>
<br>


[![](https://raw.githubusercontent.com/qb40/designs/gh-pages/0/image/11.png)](https://wolfram77.github.io)<br>
[![SRC](https://img.shields.io/badge/src-repo-green?logo=Org)](https://github.com/edubart/minilua)
[![ORG](https://img.shields.io/badge/org-nodef-green?logo=Org)](https://nodef.github.io)
![](https://ga-beacon.deno.dev/G-RC63DPBH3P:SH3Eq-NoQ9mwgYeHWxu7cw/github.com/nodef/minilua.c)
