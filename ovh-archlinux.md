# OVH - Archlinux

## Restore fucked up server

Go to rescue mode.
```bash
mount /dev/sda1 /mnt
mount /dev/sda2 /mnt/home
```
```bash
# as arch-chroot is not available
mount --bind /proc /mnt/proc
mount --bind /sys /mnt/sys
mount --bind /dev /mnt/dev
mount --bind /dev/pts /mnt/dev/pts

chroot /mnt bash
```

```bash
mkinitcpio -p linux
grub-install /dev/sda
grub-mkconfig -o /boot/grub/grub.cfg
```

```bash
netctl reenable ovh_net_eth0
```

```bash
exit
reboot
```
