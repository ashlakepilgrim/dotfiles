# Utilities

> Useful utilities and applications for screenshots, audio, image editing, and other daily tasks.

## Screenshots

Install:

```bash
sudo pacman -S scrot
```
## Audio

Install PipeWire and the required audio components:

```bash
sudo pacman -S pipewire pipewire-audio pipewire-pulse wireplumber
```

Start the required user services:

```bash
systemctl --user start pipewire
systemctl --user start pipewire-pulse
systemctl --user start wireplumber
```

Verify the audio server:

```bash
pactl info
```

After installation, reload the i3 configuration to load the audio/volume module in Polybar.