# Dotfiles Setup

> This guide explains how to setup and use the dotfiles from this repository after completing the Arch Linux installation.

## 1. Clone the Repository

Clone the repository:

```bash
git clone <repository-url>
cd dotfiles
```

Replace `<repository-url>` with the URL (HTTPS / SSH) of this repository.

Alternatively, download the repository as a ZIP file from GitHub and extract it:

```bash
unzip dotfiles-main.zip
cd dotfiles-main
```

## 2. Install Required Packages

Make sure the following packages are installed:

* i3
* Polybar
* Rofi
* Alacritty
* Picom
* Feh

If they are not already installed:

```bash
sudo pacman -S i3-wm polybar rofi alacritty picom feh
```

## 3. Copy the Dotfiles

Create the `.config` directory if it does not already exist:

```bash
mkdir -p ~/.config
```

Copy the configuration directories from the repository:

```bash
cp -r alacritty i3 picom polybar rofi wallpapers ~/.config/
```

## 4. Wallpapers

The i3 configuration currently uses one of these wallpapers:

```bash
exec_always --no-startup-id feh --bg-fill $HOME/.config/wallpapers/archlinux-tv.png
```

You can either:

### Use a Wallpaper from the Repository

Keep the included wallpapers in:

```text
~/.config/wallpapers/
```

and update the i3 configuration to use the wallpaper you want.

For example:

```bash
exec_always --no-startup-id feh --bg-fill $HOME/.config/wallpapers/anime-enchanted-garden.png
```

### Add Your Own Wallpapers

You can add your own wallpapers to:

```text
~/.config/wallpapers/
```

Then update the wallpaper path in:

```text
~/.config/i3/config
```

For example:

```bash
exec_always --no-startup-id feh --bg-fill $HOME/.config/wallpapers/my-wallpaper.jpg
```

### Store Wallpapers Somewhere Else

If you prefer to keep wallpapers outside `.config`, move the directory to your preferred location and update the `feh` command in the i3 configuration accordingly.

For example:

```bash
mkdir -p ~/Pictures/wallpapers
mv ~/.config/wallpapers/* ~/Pictures/wallpapers/
```

Then update the i3 configuration:

```bash
exec_always --no-startup-id feh --bg-fill $HOME/Pictures/wallpapers/my-wallpaper.jpg
```

## 5. Reload i3

Reload the i3 configuration:

```text
$mod + Shift + R
```

Alternatively, restart i3:

```text
$mod + Shift + E
```

and start i3 again:

```text
startx
```

## 6. Done

The dotfiles should now be applied.