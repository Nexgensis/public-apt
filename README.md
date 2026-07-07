# Nexgensis APT Repository

This repository hosts the **public APT package repository** for the Nexgensis
provisioning & deployment CLI (`nexgensis-cli`). It lets you install and keep
the tool up to date with `apt` on Debian / Ubuntu hosts.

> ℹ️ Only the compiled, **signed** `.deb` packages are served here — the CLI
> source lives in a separate private repository. Running the CLI also requires
> activation with a token for the **`nexgensis`** GitHub organization.

## Install

```bash
# 1. Trust the repository signing key
curl -fsSL https://nexgensis.github.io/public-apt/nexgensis.gpg \
  | sudo gpg --dearmor -o /usr/share/keyrings/nexgensis.gpg

# 2. Add the repository
echo "deb [signed-by=/usr/share/keyrings/nexgensis.gpg] https://nexgensis.github.io/public-apt stable main" \
  | sudo tee /etc/apt/sources.list.d/nexgensis.list

# 3. Install
sudo apt update
sudo apt install nexgensis-cli
```

Then run it:

```bash
nexgensis            # launch the provisioning wizard (browser or terminal)
nexgensis version
```

## Update

```bash
sudo apt update && sudo apt upgrade nexgensis-cli
```

## Uninstall

```bash
sudo apt remove nexgensis-cli
sudo rm -f /etc/apt/sources.list.d/nexgensis.list /usr/share/keyrings/nexgensis.gpg
```

## What gets installed

| | |
|---|---|
| Package | `nexgensis-cli` |
| Binary | `/usr/bin/nexgensis` |
| Architectures | `amd64`, `arm64` |
| Suite / component | `stable` / `main` |
| Recommends | `docker.io` |
| Signed by | `Nexgensis Packages <packages@nexgensis.com>` |
| Key fingerprint | `11D4 4F07 267B F1DD CE00  6933 CE3E 8BD9 B965 5E27` |
| Base URL | https://nexgensis.github.io/public-apt |

## Verify the signing key (optional)

```bash
curl -fsSL https://nexgensis.github.io/public-apt/nexgensis.gpg | gpg --show-keys
```

_This repository is published automatically by the `nexgensis-cli` release
pipeline; every tagged release refreshes the packages and the signed
`Release` / `InRelease` index. Do not edit the `gh-pages` branch by hand._
