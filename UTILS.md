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

## Gaming

### Steam

Steam requires the `multilib` repository.

Open the pacman configuration:

```bash
sudo nano /etc/pacman.conf
```

Uncomment:

```text
[multilib]
Include = /etc/pacman.d/mirrorlist
```

Update the package database:

```bash
sudo pacman -Syu
```

Install Steam:

```bash
sudo pacman -S steam
```

Install dependencies for Intel GPU:

```bash
sudo pacman -S mesa mesa-utils lib32-mesa vulkan-intel lib32-vulkan-intel vulkan-tools
```

Check OpenGL, Direct Rendering and Vulkan details:

```bash
glxinfo | grep "OpenGL renderer"
glxinfo | grep "direct rendering"
vulkaninfo --summary
```

### Minecraft

Install prism launcher (RECOMMENDED):

```bash
sudo pacman -S prismlauncher
```

Install official launcher from AUR:

```bash
yay -S minecraft-launcher
```
