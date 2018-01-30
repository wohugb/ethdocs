ArchLinux User Repository (AUR)
===============================

Arch Linux packages are community maintained by [Afri Schoedon](https://github.com/5chdn).

Check out the following packages on [aur.archlinux.org](https://aur.archlinux.org/packages/?O=0&K=ethereum).

-   [ethereum](https://aur.archlinux.org/packages/ethereum/) (stable,     latest release)
-   [ethereum-git](https://aur.archlinux.org/packages/ethereum-git/)     (unstable, latest develop)

To build and install the package, follow the [AUR installing package](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) instructions:

-   Acquire the tarball which contains the PKGBUILD
-   Extract the tarball
-   Run `makepkg -sri`{.sourceCode} as simple user in the directory     where the files are saved
-   Install the resulting package with `pacman -U`{.sourceCode} as     superuser

You can also use [AUR helpers](https://wiki.archlinux.org/index.php/AUR_helpers) like `yaourt`{.sourceCode} or `pacaur`{.sourceCode} to install the packages directly on your system.
