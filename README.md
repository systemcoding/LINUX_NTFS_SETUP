# Setup NTFS/LVM Drives in Linux

This only works for LVM drives currently and i am planning to update this when i have a working ntfs drive running on linux.

## For LVM Drives:
Prerequisites:
- Install ntfs-3g:
`sudo pacman -S ntfs-3g` or `sudo apt install ntfs-3g`
- Install ldmtool
`sudo pacman -S ldmtool`

- Disable fast startup in windows to allow read and write permissions in the drive.

Now create a systemd service to initialise the disks when the system boots.

```bash
[Unit]
Description=Run ldmtool create all at startup
Before=local-fs.target

[Service]
Type=oneshot
ExecStart=/usr/local/bin/ldmtool-setup.sh

[Install]
WantedBy=default.target
```
