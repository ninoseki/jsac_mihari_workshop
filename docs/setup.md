# Lab Env Setup

## Requirements

- Docker (Docker Desktop 2.0+ is recommended)
- VS Code + [Remote Development extension pack](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.vscode-remote-extensionpack)

## Setup

```bash
git clone https://github.com/ninoseki/jsac_mihari_workshop
code jsac_mihari_workshop
```

!!! info

    Follow [this instruction](https://code.visualstudio.com/docs/setup/mac#_launching-from-the-command-line) if you are unable to use `code` command.

Use the `Dev Containers: Reopen in Container` command from the Command Palette (F1, ⇧⌘P) to start the container. It will take several minutes to complete.

If everything goes well, you can use Mihari, Nuclei and jq in the container.

```bash
$ mihari -v
7.3.1

$ nuclei --version
[INF] Nuclei Engine Version: v3.1.5
[INF] Nuclei Config Directory: /home/vscode/.config/nuclei
[INF] Nuclei Cache Directory: /home/vscode/.cache/nuclei

$ jq --version
jq-1.6
```
