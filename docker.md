# Docker

<!-- vim-markdown-toc GFM -->
* [Commands](#commands)
* [Cleanup tips](#cleanup-tips)

<!-- vim-markdown-toc -->

## Commands

**pull**
`docker pull <registry>/<image>:<version>`

**push**
`docker push <registry>/<image>:<version>`

**tag**
`docker tag <source_registry>/<image>:<version> <target_registry>/<image>:<version>`

## Cleanup tips

[Keeping the whale happy: How to clean up after Docker](https://getintodevops.com/blog/keeping-the-whale-happy-how-to-clean-up-after-docker)

- Tip: Get permission denied when running docker commands?:

```bash
sudo usermod -aG docker $USER
```
