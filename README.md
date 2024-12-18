JuNest
======

### I KEEPED THE IMPORTANT THINGS ONLY IN README SO YOU CAN CHECK THE ORIGINAL REPO TO CHECK THE WHOLE README.

Installation
============

## Installation from git repository ##

```sh
git clone https://github.com/mrx7014/acrh.git
mv acrh junest
cp junest ~/.local/share
export PATH=~/.local/share/junest/bin:$PATH
```

Quickstart
==========

Setup environment
-----------------

```sh
junest setup
```

The script will download the image from the repository and will place it to the default directory `~/.junest`.

Access to environment
---------------------

```sh
junest
```

You can use the command `sudo` to acquire fakeroot privileges and
install/remove packages.

Alternatively, you can access fakeroot privileges without using `sudo` all the
time with the `-f` (or `--fakeroot`) option:

```sh
junest -f
```

Another execution mode is via [Proot](https://wiki.archlinux.org/index.php/Proot):

```sh
junest proot [-f]
```

PRoot based
-----------
[Proot](https://wiki.archlinux.org/index.php/Proot) represents a portable
solution which allows unprivileged users to execute programs inside a sandbox
and works well in most of GNU/Linux distros available.

In order to run JuNest via Proot:

- As normal user - Allow to make basic operations: `junest proot`

- As fakeroot - Allow to install/remove packages: `junest proot -f`

In `proot` mode, the minimum recommended Linux kernel for the host OS is 2.6.32 on x86 (64 bit)
and ARM architectures. It is still possible to run JuNest on lower
2.6.x host OS kernels but errors may appear, and some applications may
crash. For further information, read the [Troubleshooting](#troubleshooting)
section below.

Advanced usage
==============
## Build image ##
You can build a new JuNest image from scratch by running the following command:

```sh
junest build [-n]
```

The script will create a directory containing all the essentials
files in order to make JuNest working properly (such as `pacman` and `proot`).
The option `-n` will skip the final validation tests if they are not needed.
Remember that the script to build the image must run in an Arch Linux OS with
arch-install-scripts and the base-devel packages installed.
To change the build directory just use the `JUNEST_TEMPDIR` (by default /tmp).

After creating the image `junest-x86_64.tar.gz` you can install it by running:

```sh
junest setup -i junest-x86_64.tar.gz
```

For more details, you can also take a look at
[junest-builder](https://github.com/fsquillace/junest-builder)
that contains the script and systemd service used for the automatic building
of the JuNest image.

- [How to run services using Systemd](https://github.com/fsquillace/junest/wiki/How-to-run-services-using-Systemd)
