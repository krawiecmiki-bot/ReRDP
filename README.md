<div align="center">

<img src="./org.rerdp.ReRdp.svg" alt="ReRDP logo" width="180">

# ReRDP

**Run multiple local Linux desktops in separate RDP windows.**

[![License](https://img.shields.io/badge/license-Other-blue.svg)](./LICENSE.md)
[![Platform](https://img.shields.io/badge/platform-Linux-lightgrey.svg)](#requirements)
[![Status](https://img.shields.io/badge/status-Active-success.svg)](#overview)

[Features](#features) · [Requirements](#requirements) · [Installation](#installation) · [Usage](#usage) · [Contributing](#contributing)

</div>

## Overview

ReRDP is a lightweight project for opening several local Linux accounts in individual Xorg desktop windows over loopback RDP.

> ReRDP is not a virtual machine manager. It connects RDP client windows to local `xrdp` sessions running on the same computer.

## Features

- Separate desktop window for each local Linux account
- Native loopback RDP sessions through `xrdp`
- Individual Xorg sessions instead of a shared desktop
- Simple setup with per-user isolation
- Lightweight alternative to traditional VM-based workflows

## Requirements

<!-- TODO: Replace these placeholders with the exact supported distributions and package versions. -->

- Linux desktop environment
- Xorg display server
- `xrdp` and an RDP client
- A local Linux account for each desired desktop session
- <!-- TODO: Add package manager and supported distribution -->

## Installation

<!-- TODO: Add the real installation commands below. -->

```bash
# Clone the repository
git clone https://github.com/krawiecmiki-bot/ReRDP.git
cd ReRDP

# TODO: Add setup command
```

## Usage

<!-- TODO: Add the actual executable name and command-line flags. -->

```bash
# TODO: Start ReRDP
# rerdp
```

<!--
Screenshot placeholder:
Add a screenshot or recording here once available:

<div align="center">
  <img src="./docs/images/reRDP-preview.png" alt="ReRDP preview" width="800">
</div>
-->

## How It Works

```text
Local Linux account → xrdp session → loopback RDP → Separate desktop window
```

## Contributing

Contributions are welcome. Please open an issue before major changes and include steps to reproduce for bug reports.

## License

See [LICENSE.md](./LICENSE.md) for the full license text.

<div align="center">

**ReRDP** — separate desktops, one local machine.

</div>
