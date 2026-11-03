# Seanime Flatpak

Unofficial Flatpak packaging of [Seanime](https://seanime.app) - a self-hosted anime and manga media server with a desktop app.

## Installation

### From the repository (recommended, supports `flatpak update`)

```bash
flatpak remote-add --user --if-not-exists seanime https://imshinyu.github.io/seanime-flatpak/seanime.flatpakrepo
flatpak install --user seanime io.github.seanime.Seanime
```

The `.flatpakrepo` file embeds the repository's GPG public key, so Flatpak verifies the signature of every update automatically.

### From a bundle

Download the latest `Seanime.flatpak` from [Releases](https://github.com/imshinyu/seanime-flatpak/releases) and install it:

```bash
flatpak install --user ~/Downloads/Seanime.flatpak
```

Then run it with:

```bash
flatpak run io.github.seanime.Seanime
```

## Permissions

The manifest grants:

- Network access
- Wayland with an X11 fallback
- PipeWire/PulseAudio output
- GPU acceleration (`--device=dri`)
- Read/write access to `xdg-download`, `xdg-videos` and `xdg-music`
- Desktop notifications and the StatusNotifier tray

If your library lives somewhere else, grant it explicitly instead of opening the whole home directory:

```bash
flatpak override --user --filesystem=/path/to/anime io.github.seanime.Seanime
```

## Updating

A scheduled workflow checks the upstream Seanime GitHub releases every six hours. When a new version is published it updates the manifest and metainfo, commits the change, and triggers a new build. To update an installed copy manually:

```bash
flatpak update
```

The app's built-in updater is intentionally disabled; use `flatpak update` instead.

## Repository signing

The Flatpak repository and its summary are signed with a dedicated GPG key in CI. The public key is published in [`seanime.flatpakrepo`](https://imshinyu.github.io/seanime-flatpak/seanime.flatpakrepo), so `flatpak remote-add` trusts it without any extra steps.

## Disclaimer

This is an **unofficial** community package. Seanime is developed by [5rahim](https://github.com/5rahim/seanime).
