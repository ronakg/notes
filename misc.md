# Misc

<!-- vim-markdown-toc GFM -->

* [Tips](#tips)
  * [SSH Jumphost](#ssh-jumphost)

<!-- vim-markdown-toc -->

## Tips

### SSH Jumphost

- Connect to `targethost` via `jumphost` through SSH.

```bash
  $ ssh -t jumpuser@jumphost.domain ssh -t targetuser@targethost.domain
```

- Make above seamless and automatic by adding following to `~/.ssh/config`

```
Host jumphost
  Hostname jumphost.domain
  User jumpuser

Host targethost
  ProxyCommand ssh -W %h:%p jumphost
```
