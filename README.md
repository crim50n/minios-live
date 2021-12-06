[![MiniOS](images/minios.png)](http://t.me/minios_news)

:us:

These scripts build a bootable MiniOS ISO image.

Using minios-live, you can build:

*Debian 9, 10 with Fluxbox environment (analogous to Slax <https://www.slax.org/>).*

*Debian 9, 10, 11 and Ubuntu 20.04 with Xfce4 environment.*

*Experimentally added support for the Cinnamon environment for all versions of distributions.*

To build, you need to change the parameters in the **linux-live/buildconfig** file to build the required option, then start the build: `./install -`

It is advisable to use Ubuntu 20.04 for build, since in this system you can build MiniOS based on Debian 9,10,11 and Unbuntu 20.04. If you have a different system installed, use docker. 

For installation use **install** - script for guided installation, **autoinstall** - script for automatic installation.

**Never run scripts from linux-live! They will break your system.**

**Supported commands:** `setup_host build_bootstrap build_chroot build_live build_modules build_iso`

*setup_host* - installing packages required for building on the host

*build_bootstrap* - install a minimal system using debootstrap

*build_chroot* - installation of the rest of the components required to start the system

*build_live* - build initramfs and squashfs image

*build_modules_chroot* - building modules

*build_iso* - build the final ISO image

**Syntax:** `./install [start_cmd] [-] [end_cmd]`
- launch from start_cmd to end_cmd
- if start_cmd is omitted, all commands are executed starting from the first
- if end_cmd is omitted, all commands up to the last are executed
- enter one command to run a specific command
- enter '-' as the only argument to run all commands

        Examples: ./install build_bootstrap - build_chroot
                  ./install - build_chroot
                  ./install build_bootstrap -
                  ./install build_iso
                  ./install -

To build with docker, create a build folder in your home folder, put minios-live there, run 01-runme.sh from the docker folder. This action will install the required programs and create an image. To start the build, edit for yourself and run 02-build.sh. Sample file content:

`docker run --rm -it --name mlc --privileged -v /home/user/build:/build local/mlc /build/minios-live/install -`

Author: crims0n <https://t.me/minios_news>
