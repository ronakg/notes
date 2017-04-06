# Vim and NeoVim

## Table of Contents

<!-- vim-markdown-toc GFM -->
* [Tips](#tips)
* [Vim](#vim)
* [NeoVim](#neovim)
    * [Building](#building)
    * [C/C++ Support](#cc-support)

<!-- vim-markdown-toc -->

## Tips

- Get all the diff blocks from other file `:%diffget`
- Put all the diff blocks to other file `:%diffput`

## Vim

- Only substitute part of the matched string
    - `\zs` to ignore anything coming in front of it
    - `\ze` to ignore anything coming after it

```vim
" foobar -> foobaz
%s/foo\zsbar/baz/

" foobar -> bazbar
%s/foo\zebar/baz/
```

## NeoVim

### Building

- [Official Instructions from NeoVim](https://github.com/neovim/neovim/wiki/Building-Neovim)

```bash
git pull https://github.com/neovim/neovim.git
rm -r build
make clean
make CMAKE_BUILD_TYPE=Release
make install
```

### C/C++ Support

- Build llvm with clang support:

Mac:

```bash
brew install llvm --with-clang
```

Linux:

```bash
apt-get install clang
```
