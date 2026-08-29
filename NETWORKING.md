# Network

## UFW

### Install

```bash
sudo pacman -S ufw
```

### Enable

```bash
sudo systemctl enable --now ufw
```

### Configure

```bash
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw enable
```

### Status

```bash
sudo ufw status verbose
sudo ufw status numbered
```

### Allow a port

```bash
sudo ufw allow <port>/tcp
sudo ufw allow <port>/udp
```

### Delete an existing UFW rule

```bash
sudo ufw delete allow <port>/tcp
sudo ufw delete allow <port>/udp
```

## Tailscale

### Install

```bash
sudo pacman -S tailscale
```

### Enable

```bash
sudo systemctl enable --now tailscaled
```

### Status

```bash
tailscale status
```

### Connect

```bash
sudo tailscale up
```

### Ping another device

```bash
tailscale ping <tailscale-ip>
```

### Disconnect

```bash
sudo tailscale down
```

### Disable

```bash
sudo tailscale down
sudo systemctl disable --now tailscaled
```