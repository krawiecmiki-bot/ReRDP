<div align="center">

<img src="./org.rerdp.ReRdp.svg" alt="ReRDP logo" width="180">

# ReRDP

**Run multiple local Linux desktops in separate RDP windows.**

[![License](https://img.shields.io/badge/license-Other-blue.svg)](./LICENSE.md)
[![Platform](https://img.shields.io/badge/platform-Linux-lightgrey.svg)](#requirements)
[![Status](https://img.shields.io/badge/status-Active-success.svg)](#Releases)

[Features](#features) · [Requirements](#requirements) · [Installation](#Download-and-install) · [Usage](#Using-ReRDP) · [License and other](#License)





 ## Cordial is not yet supported by Revolution Macro, please wait for an update, at the moment, it is only possible to run one client using [Sober](https://github.com/vinegarhq/sober)
 ## ReRDP has not been tested on Niri, Hyprland, Sway or MangoWC, so compatibility is not guaranteed. For now, using a desktop environment is recommended. Support for window managers will be added in a future release
 (probaly in V1.0 release).




<p align="center">
  Independent Linux desktop sessions, each running in its own window and local account.
</p>

<p align="center">
  <strong>Version 0.4.0</strong> · Fedora recommended · MATE and Xfce · PolyForm Noncommercial License 1.0.0
</p>



ReRDP creates and manages local Linux user accounts, then launches a separate graphical desktop for each account in a
TigerVNC viewer window. It is not a virtual machine. Your normal GNOME desktop remains available while the session runs.

Each desktop uses its own Xvnc display and a local Unix socket. The viewer does not open an RDP or VNC TCP port. X11
input sent to one session's display stays in that display, isolated from the host display and other ReRDP sessions.
Programs with privileged or device-level access can act outside this boundary. TigerVNC also does not provide raw
relative mouse capture for every game, so some games may still have inconsistent mouse behavior.


!                           
                             ReRDP is 100% free, open-source software. It may be used for any purpose, with the exception of commercial or unlawful use.
## Features

- Create, launch, stop, configure, and delete managed Linux desktop sessions.
- Give each session its own Linux account and home directory.
- Use MATE or Xfce, and change a session's desktop while it is stopped.
- Choose from 13 dark themes with matching gradients and accents, including the Revolution blue, cyan, pink, and gray palette.
- Optionally launch Cordial and Revolution Macro when a session starts.
- Keep diagnostic logging off by default; enable it in Settings when troubleshooting.
- Update from a local release archive while keeping session accounts, settings, and data.
- Keep session connections local through Unix sockets; ReRDP does not change your login manager or normal GNOME session.

## Supported Linux distributions

The installer includes dependency maps for Fedora, Arch Linux, and Debian-based distributions, including Debian and
Ubuntu. Fedora is recommended: ReRDP was developed and tested primarily on Fedora (Fedora 45). The application needs
GTK 4 and libadwaita 1.5 or newer, so availability depends on the distribution release and enabled repositories.

## Requirements

- A supported Fedora, Arch Linux, Debian, or Ubuntu installation with systemd or a compatible Linux service setup.
- GTK 4 and libadwaita 1.5 or newer for the graphical app.
- TigerVNC's `Xvnc` server and a VNC viewer.
- At least one supported session desktop: MATE or Xfce.
- D-Bus, X authentication utilities, and the account/service tools listed by the installer.

ReRDP checks for required components before installation, lists missing dependencies, and asks before installing system
packages. It uses DNF on Fedora, pacman on Arch, and APT on Debian-based systems. It does not install or replace a display
manager.

## Download and install

1. Download the **ReRDP Beta 1 0.4** release archive from the GitHub Releases page.
2. Extract it and open a terminal in the extracted `ReRdp-0.4.0` folder.
3. Run the installer:

   ```bash
   ./install.sh
   ```

The installer checks dependencies and asks before installing missing packages. It may request administrator
authentication for package installation and system setup. Once installed, open **ReRDP** from the applications menu or
run:

```bash
rerdp
```

To remove the application but keep your sessions and accounts, run `./install.sh --uninstall` from the release folder.
Delete each managed session from ReRDP first if you also want to remove its Linux account and home directory.

## Using ReRDP

1. Open ReRDP and click **+** to create a session.
2. Enter a session name, Linux username, and account password. Choose MATE or Xfce.
3. Click **Launch** to open that account's desktop in its own window. Use **Stop** to end the session.
4. Use the session's settings button to rename it, change its desktop while stopped, configure startup apps, or delete it.
5. Open the three-dot menu and choose **Settings** to change the app theme, logging, password policy, or update the app.

The Linux account password is set when the session is created. TigerVNC does not ask for that password each time the local
viewer connects: the viewer uses the session's permission-protected Unix socket on the same machine.

Revolution Macro and Cordial are optional separate applications. Configure their launch commands in the session's
startup app settings if you want them to start with a desktop. ReRDP does not bundle either project.

## Updates and logs

To install a bugfix or release archive, open **Settings → Update from a file** and choose the `.tar.gz` archive. The
updater validates the archive and keeps your sessions, accounts, and settings. It does not require running the terminal
installer again.

Logging is disabled by default. Turn on **Settings → Save logs**, then stop and relaunch the session to capture its next
startup. Session logs are stored under `/var/log/rerdp/<session-id>/session.log`; viewer diagnostics are saved to
`viewer.log` when the viewer closes. Use **Settings → Log folder → Open** to inspect the log directory.

## Troubleshooting

- **Black or empty desktop:** check that the selected desktop is installed and inspect that session's `session.log`.
  Xfce sessions start through `xfce4-session` because Xvnc already provides their X server.
- **Mouse feels unusual in a game:** VNC pointer input is absolute, and some games expect raw relative mouse capture.
  This is a limitation of the viewer/display path and can vary by game.
- **No log file:** logging is off by default. Enable it, then stop and relaunch the session; the log is created on startup.
- **Missing dependency:** rerun the installer and review its dependency report. Confirm the package install prompt only
  after reviewing the package manager command it shows.

## License

ReRDP is licensed under the **PolyForm Noncommercial License 1.0.0**. See [LICENSE](LICENSE) for the official license text.

## Acknowledgements

Thank you to the authors and communities behind:

- [Cordial](https://github.com/luohoa97/cordial), the Roblox runtime ReRDP users can run inside a managed desktop session; follow Cordial's project for its installation and Roblox download steps.
- [Revolution Macro](https://github.com/nosyliam/revolution-macro), which can also be configured as a session startup app.
  Revolution Macro's Linux build and support information are shared in the [Revolution Macro Discord](https://discord.gg/revolutionmacro).

Cordial and Revolution Macro are separate projects and are not bundled or redistributed by ReRDP.

## Development and tests

Build a release archive and run the non-destructive test suite from the project directory:

```bash
./tools/make-release.sh
python3 -m unittest discover -s tests
```

The suite does not create system accounts or install packages. The integration, installer, and GUI smoke tests change
system state and should only be run on a disposable machine after reviewing their safeguards in the test files.

RDP is 100% free, open-source software. It may be used for any purpose, with the exception of commercial or unlawful use.
