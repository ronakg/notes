# Misc

<!-- vim-markdown-toc GFM -->

* [Tips](#tips)
  * [SSH Jumphost](#ssh-jumphost)

<!-- vim-markdown-toc -->

## Tips

### SSH Jumphost

- Connect to `targethost` via `jumphost` through SSH.

```
Host jumphost
  Hostname jumphost.domain
  User jumpuser

Host targethost
  ProxyCommand ssh -W %h:%p jumphost
```
