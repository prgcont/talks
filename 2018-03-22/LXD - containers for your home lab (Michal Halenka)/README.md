# LXD - containers for your home lab (Michal Halenka)

## Preparation

To avoid possible network issue it is a good think to get VirtualBox machine and prefetch VM images needed for hands-on part of this presentation.

```bash
# prepare working directory
mkdir prgcont
cd prgcont

# get Vagrantfile
wget 'https://raw.githubusercontent.com/prgcont/talks/master/2018-03-22/LXD%20-%20containers%20for%20your%20home%20lab%20(Michal%20Halenka)/Vagrantfile'

# get Vagrant plugin for disksize changes
vagrant plugin install vagrant-disksize

# Fedora porn
export VAGRANT_DEFAULT_PROVIDER=virtualbox

# run VM to get OS images upfront
vagrant up

# suspend your VM till PragueContainers meetup
vagrant suspend
```
