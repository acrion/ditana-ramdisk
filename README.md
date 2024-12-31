# ditana-ramdisk

This package provides a user-specific RAM disk service for Ditana GNU/Linux, offering fast, temporary storage with enhanced privacy and organization.

## Description

`ditana-ramdisk` creates a temporary storage space in RAM, similar to `/tmp`, but with several key advantages:

- User-specific: Mounted in the user's runtime directory (`$XDG_RUNTIME_DIR`) and symlinked to `$HOME/RAMDisk` for easy access.
- Clean and organized: Exclusively reserved for user data, free from system service files typically found in `$XDG_RUNTIME_DIR`.
- Enhanced privacy: Unlike `/tmp`, which is globally accessible, this RAM disk is specific to the user, ensuring better control over access rights.
- Convenient access: An environment variable, `$RAMDISK`, is set for easy reference in scripts or applications.
- Desktop integration: For desktop users, the RAM disk is integrated into the file manager for quick access.

## Features

- Fast temporary storage ideal for tasks such as multimedia processing or caching.
- Automatically cleared at logout, ensuring data privacy.
- Seamless integration with the Thunar file manager (if installed).
- Systemd service for automatic setup and management.

## Installation

This package is typically installed by default through the Ditana Installer. For manual installation:

```bash
sudo pacman -S ditana-ramdisk
```

## Usage

Once installed, the RAM disk is automatically set up at user login. You can access it through:

1. File manager: Look for "RAM Disk" in your bookmarks (if using Thunar).
2. Command line: Navigate to `~/RAMDisk` or use the `$RAMDISK` environment variable.

Example usage in a script:

```bash
cp large_file.dat $RAMDISK/
# Process the file in RAM
rm $RAMDISK/large_file.dat
```

## Configuration

The RAM disk is configured to be created in `/run/user/$UID/ramdisk`. This location is set in:

- `/etc/environment.d/90-ditana-ramdisk.conf` for systemd context
- `/etc/profile.d/ditana-ramdisk.sh` for user shell sessions

You can modify these files if you need to change the default location.

## Uninstallation

When removing the package, the systemd service will be disabled and the Thunar bookmark (if present) will be removed.

```bash
sudo pacman -R ditana-ramdisk
```

## Dependencies

- systemd

For more information about Ditana GNU/Linux, visit [https://ditana.org](https://ditana.org)
