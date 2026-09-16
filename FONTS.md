# Fonts

> Fonts that I prefer in some applications.

## Emojis

```bash
sudo pacman -S noto-fonts-emoji
fc-cache -fv
```

## Inconsolata

```bash
mkdir -p ~/.local/share/fonts/ttf && cp fonts/Inconsolata/*.ttf ~/.local/share/fonts/ttf/
fc-cache -fv
```