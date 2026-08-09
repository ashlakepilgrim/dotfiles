# Development Dependencies

> This guide covers the development tools and services used with this setup.

## 1. Git

Install Git and Less:

```bash
sudo pacman -S git less
```

Generate an SSH key:

```bash
ssh-keygen -t ed25519 -C "your-email@example.com"
```

Start the SSH agent:

```bash
eval "$(ssh-agent -s)"
```

Add the SSH key:

```bash
ssh-add ~/.ssh/id_ed25519
```

Display the public key:

```bash
cat ~/.ssh/id_ed25519.pub
```

Copy the output and add it to your GitHub SSH keys.

Test the SSH connection:

```bash
ssh -T git@github.com
```

## 2. Visual Studio Code

Install Visual Studio Code from the AUR:

```bash
yay -S visual-studio-code-bin
```

## 3. PostgreSQL & pgAdmin

Install PostgreSQL:

```bash
sudo pacman -S postgresql
```

Initialize the PostgreSQL database:

```bash
sudo -iu postgres initdb -D /var/lib/postgres/data
```

Enable and start the PostgreSQL service:

```bash
sudo systemctl enable --now postgresql
```

Check the service status:

```bash
systemctl status postgresql
```

Search the AUR for pgAdmin:

```bash
yay -Ss pgadmin
```

Install the desktop version:

```bash
yay -S pgadmin4-desktop-bin
```