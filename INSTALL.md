# Arch Linux Installation

> **Warning:** This guide is tailored to my setup. Verify disk names, CPU microcode, timezone, and partition layout before running commands.

## 1. Check UEFI, Network & Set Timezone

```bash
cat /sys/firmware/efi/fw_platform_size
ping -c 3 8.8.8.8
timedatectl
timedatectl list-timezones | grep Asia/Tokyo
timedatectl set-timezone Asia/Tokyo
timedatectl status
hwclock --systohc
```

## 2. Partition Disk

```bash
lsblk
cfdisk /dev/sda
```

Partitions:

```text
/dev/sda1   EFI System       512M
/dev/sda2   Linux swap       8G
/dev/sda3   Linux filesystem ~457G
```

## 3. Format & Mount

```bash
mkfs.fat -F32 /dev/sda1
mkswap /dev/sda2
swapon /dev/sda2
mkfs.ext4 /dev/sda3

mount /dev/sda3 /mnt
mkdir /mnt/boot
mount /dev/sda1 /mnt/boot
```

## 4. Install Base System

```bash
pacstrap /mnt base linux linux-firmware base-devel linux-headers intel-ucode networkmanager nano vim
genfstab -U /mnt >> /mnt/etc/fstab
arch-chroot /mnt
```

## 5. Locale & Timezone

```bash
nano /etc/locale.gen
```

Uncomment:

```text
en_US.UTF-8 UTF-8
```

Then:

```bash
locale-gen
echo "LANG=en_US.UTF-8" > /etc/locale.conf
ln -sf /usr/share/zoneinfo/Asia/Tokyo /etc/localtime
```

## 6. Hostname

```bash
echo archmachine > /etc/hostname
nano /etc/hosts
```

Add:

```text
127.0.0.1   localhost
::1         localhost
127.0.1.1   archmachine.localdomain archmachine
```

Set root password:

```bash
passwd
```

Enable NetworkManager:

```bash
systemctl enable NetworkManager
```

## 7. Bootloader

```bash
pacman -S grub efibootmgr
grub-install --target=x86_64-efi --efi-directory=/boot --bootloader-id=GRUB
grub-mkconfig -o /boot/grub/grub.cfg
```

## 8. User

```bash
useradd -m -G wheel -s /bin/bash acorn
passwd acorn
EDITOR=nano visudo
```

Uncomment:

```text
%wheel ALL=(ALL:ALL) ALL
```

Then:

```bash
exit
umount -R /mnt
reboot
```

## 9. Update System

Log in as the user you created.

Then:

```bash
sudo pacman -Syu
```

## 10. Desktop

```bash
sudo pacman -S xorg-server xorg-xinit xorg-xrandr i3-wm picom rofi alacritty feh polybar
sudo pacman -S papirus-icon-theme
```

Install fonts:

```bash
sudo pacman -S ttf-terminus-nerd
```

Install Fastfetch:

```bash
sudo pacman -S fastfetch
```

Install Htop:

```bash
sudo pacman -S htop
```

Install Zip & Unzip:

```bash
sudo pacman -S zip unzip
```

Install Thunar & Related Packages:

```bash
sudo pacman -S thunar gvfs thunar-volman udisks2
```

Setup AUR:

```bash
sudo pacman -S git
git clone https://aur.archlinux.org/yay.git
cd yay
makepkg -si
```

Install Brave Browser:

```bash
yay -S brave-bin
```

Create `.xinitrc`:

```bash
echo "exec dbus-run-session i3" > ~/.xinitrc
```

Start i3:

```bash
startx
```