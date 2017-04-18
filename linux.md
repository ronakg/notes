# Linux

<!-- vim-markdown-toc GFM -->
* [Tips](#tips)
    * [Setup SSH tunnel via intermediate host](#setup-ssh-tunnel-via-intermediate-host)
* [Tools](#tools)
    * [Parse json](#parse-json)
    * [Create temporary files](#create-temporary-files)
* [Issues](#issues)

<!-- vim-markdown-toc -->

## Tips

### Setup SSH tunnel via intermediate host

```bash
ssh -v -L <localport>:<target_host>:<target_port> -N <intermediate_host>
ssh -v -L 8888:10.0.0.231:443 -N centbuild03
```

## Tools

- Don't show errors in grep: `-s` or `--no-messages` to suppress errors.
- wget don't download file if already downloaded and continue partial downloads - `wget -c -N`
- Remove an entry from ssh known_hosts -

```bash
ssh-keygen -f "/home/ronakg/.ssh/known_hosts" -R <IP:1.1.1.1>
```

### Parse json

Use `jq` to parse any json text into json objects. https://stedolan.github.io/jq/

### Create temporary files

Create a temporary file in `<dir>`. `<template>` must have at least 3 `XXX`. Pass `-d` to create a temporary directory.

`mktemp -p <dir> -t <template>`

## Issues

- **Error about not able to set locale**

    ```bash
    locale: Cannot set LC_CTYPE to default locale: No such file or directory
    locale: Cannot set LC_ALL to default locale: No such file or directory
    ```

    **Fix**: Run following command. This will update `/etc/default/locale` file with correct values.

    ```bash
    ❯ sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8

    ❯ cat /etc/default/locale
    LANG=en_US.UTF-8
    LC_ALL=en_US.UTF-8
    ```

- **Core file not getting generated after crash**

    Set the ulimit to unlimited to fix this.
    ```ulimit -c unlimited```

