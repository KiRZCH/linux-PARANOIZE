# Linux-5.19.2 PARANOIZE Kernel
> Author: Entropic Raven [[GPG Key](keys/pgp/DA01B4CB62591392EA4B0D9325056AD4B82B6AD6.asc)] \
> Version: 5.19.2-1 \
> Name: Paranoid Raven \
> Based on: [linux-5.19.2-zen-1-zen](https://github.com/zen-kernel/zen-kernel)

---------------------------------


## **How to install**
<br>

### **Install Binaries**

First of all, keep in mind that this kernel is been optimized for [**Arch Linux**](https://archlinux.org/download/) based Distro, such as [*Manjaro*](https://manjaro.org/download/), [*Garuda*](https://garudalinux.org/downloads.html), and so on! \
<br>
If you are on Other Distro, check how to convert from PKG to your Package Manager working extension: `.deb` (for Debian/Ubuntu based) and `.rpm` (for RHEL/Fedora/CentOS based)

For installing binaries head over the Release Page and download the files: <br>

1. Main Files
    - `linux-PARANOIZE-5.19.2-1-x86_64.pkg.tar.zst` <br>
    *Main Kernel package*
    - `linux-PARANOIZE-headers-5.19.2-1-x86_64.pkg.tar.zst` <br>
    *Kernel Headers package*
2. Signature Files (*optional*)
    - `linux-PARANOIZE-5.19.2-1-x86_64.pkg.tar.zst.sig`
    - `linux-PARANOIZE-headers-5.19.2-1-x86_64.pkg.tar.zst.sig`

#### ***How to verify digital signature*** (*optional*)

For verify signatures, in this case, PGP signatures you need a tool called `gpg`, it's pre-installed in your distro or, if you have Windows ([Gpg4win](https://www.gpg4win.org/)) or MacOS ([GPG Suite](https://gpgtools.org)), you can download it.

After the download, generate your keypair by typing this on your terminal (or you can use the guided GUI):
```bash
gpg --full-gen-key
```
follow the guide and it will generate the key to verify the PKG.
now you have to import [*my* key](keys/pgp/DA01B4CB62591392EA4B0D9325056AD4B82B6AD6.asc), download the file, the `.sig` file that matches the name and type this into the terminal
```bash
gpg --import DA01B4CB62591392EA4B0D9325056AD4B82B6AD6.asc
```
NOW, you can verify the PKG, by typing this in the same directory of the PKG:

```bash
gpg --verify linux-PARANOIZE-5.19.2-1-x86_64.pkg.tar.zst.sig linux-PARANOIZE-5.19.2-1-x86_64.pkg.tar.zst
```
Remember[^1].

If you something like this this:
```text
gpg: Signature made Fri 19 Aug 2022 02:45:12 AM CEST
gpg:                using EDDSA key 469E06A170620706072405AE47761D0398CB52A7
gpg: Good signature from "Entropic Raven (Github) <22600240+KiRZCH@users.noreply.github.com>" [ultimate]
```
Everything is OK, you can install it.
if you see something else, try dowloading the files again or dm to me!<br>
**Do the same for Kernel and Headers!**

#### ***Installing***
Arch Linux:
```bash
sudo pacman -U linux-PARANOIZE-5.19.2-1-x86_64.pkg.tar.zst
sudo pacman -U linux-PARANOIZE-headers-5.19.2-1-x86_64.pkg.tar.zst
```

**Done!** :smile:


## Compiling the sources

this is more advanced, but it will grant you to customize the installation, by tweaking `PKGBUILD`, `Makefile` and `config`
- `PKGBUILD` : Used by `makepkg` to build (with the `build()` function) the source and making the `.pkg.tar.zst` (with the `_package()` function)
- `Makefile` : Is the file used to manually build the source with the `make` comand
- `config` : Is the kernel configuration file, tweaking this will sure you to perform a custom installation based on your preferences, you can edit it by extracting the source with `makepkg -o`, `cd` in the source directory and perform a `make menuconfig`

Now, perform installation with:
```bash
makepkg -si
```

- -s : Install the dependences for build the source
- -i : Install the package (`pacman -U`)

[^1]: first the `.sig` file, then the `.zst`

