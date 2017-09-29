# Python

<!-- vim-markdown-toc GFM -->
* [Language](#language)
    * [Lists](#lists)
    * [Hash tables (Sets and Dictionaries)](#hash-tables-sets-and-dictionaries)
    * [Deque](#deque)
* [Third-party tools](#third-party-tools)

<!-- vim-markdown-toc -->

## Language

- `sys.getrefcnt()` to get reference count for any object
- `sys.getsizeof()` to get sizeof the object

### Lists

* List uses `malloc()`, `realloc()` and `free()`.
* Fixed length array of pointers
* Starts with size 4 and grows organically - 4, 8, 16, 25, ...
* `pop()` is very cheap because no copy is involved for `realloc()`
* `insert`, `pop` and `del` with index are very expensive as Lists are arrays
* Use `collections.deque()` which is optimized for double ended operations, but it's slow at indexed access
* `range(n)` allocates EXACTLY n spaces
* `[None] * n` will pre-size

### Hash tables (Sets and Dictionaries)

* Sets and dicts don't have a hash function.
* Hash is in the object that's being stored in the container (`__hash__`)
* Base size of hash table is 8 rows
* Only restriction for any object to be used in sets or dicts is it's hashability

### Deque

* `maxlen` is great for deques.

## Third-party tools

- Better REPL: https://github.com/jonathanslenders/ptpython
