# Python

## Language

### Lists
* List uses `malloc()`, `realloc()` and `free()`.
* Fixed length array of pointers
* Starts with size 4 and grows organically - 4, 8, 16, 25, ...
* `pop()` is very cheap because no copy is involved for `realloc()`
* `insert`, `pop` and `del` with index are very expensive as Lists are arrays
* Use `collections.deque()` which is optimized for double ended operations, but it's slow at indexed access

## Third-party tools

- Better REPL: https://github.com/jonathanslenders/ptpython
