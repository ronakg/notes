# Linux

<!-- vim-markdown-toc GFM -->
* [Issues](#issues)

<!-- vim-markdown-toc -->

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

