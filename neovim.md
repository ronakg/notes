# NeoVim

## Building

- [Official Instructions from NeoVim](https://github.com/neovim/neovim/wiki/Building-Neovim)

```bash
git pull
rm -r build
make clean
make CMAKE_BUILD_TYPE=Release
make install
```

## C/C++ Support

- Build llvm with clang support:

Mac:

```bash
brew install llvm --with-clang
```

Linux:

```bash
apt-get install clang
```
