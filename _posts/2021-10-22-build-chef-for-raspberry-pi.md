---
title: Build Chef For Raspberry Pi
category: devops
layout: post
---

Chef is a configuration management software that can automate many DevOps tasks. It supports a variety of platforms. However, it does _not_ have official support for ARM based platforms, such as Raspberry Pi. This article describes how to compile Chef from source on a Raspberry Pi.

<!--more-->

---

**Note** Chef now [provides official packages](https://www.chef.io/downloads/tools/infra-client?os=debian) for aarch64.

---

[This website](https://mattray.github.io/arm/) has a page that publishes 32-bit Chef packages for ARMv6 and ARMv7, including the instructions about how to build Chef from source. Now that Raspberry Pi 3 and 4 supports 64-bit computing. Based on [the page on mattray's website](https://mattray.github.io/2019/05/18/chef-15-on-arm), this article talks about how to build Chef for 64-bit ARM systems.

I'm running 64-bit Ubuntu 21.10 on my Raspberry Pi 4. The instructions here should work for other Ubuntu and Debian distros (including Raspberry Pi OS).

---

**A Note on Shell Prompt Conventions**

In this article, code blocks containing shell commands starts with some prompt strings. The conventions are

- `#` means root shell. Normally you run commands as root by prepending `sudo`.
- `$` means non-root user shell.
- Some lines explicitly includes the current working directory to avoid ambiguity.

---

# Install Dependencies

Before we start, first we need to install some dependencies, using the following command

```
# apt-get update
# apt-get upgrade
# apt-get install -y autoconf bison build-essential fakeroot git libreadline-dev libssl-dev zlib1g-dev
```

# Install Ruby

We need to Ruby to build Chef and other tools, depending on the distro, you may or may not have the right version of Ruby in the package manager source. Therefore it is recommended to build Ruby from source, using [`rbenv`](https://github.com/rbenv/rbenv). The following lines clones `rbenv` repo and compiles it. The last two lines intializes the current shell with `rbenv`.

```
$ git clone --depth=1 https://github.com/rbenv/rbenv.git ~/.rbenv
$ cd ~/.rbenv && src/configure && make -C src
$ export PATH="$HOME/.rbenv/bin:$PATH"
$ eval "$(rbenv init -)"
```

Using `rbenv`, we can build Ruby from source using `ruby-build`, a plugin of `rbenv`. As of November 2021, the latest stable version of Ruby is `2.7.4`. You can run `rbenv install --list` to get a list of current stable versions. It takes a few minutes to build Ruby from source. Use `--verbose` option to view the build commands output.

```
[~/.rbenv]$ mkdir plugins
$ git clone --depth=1 https://github.com/rbenv/ruby-build.git "$(rbenv root)"/plugins/ruby-build
$ rbenv install --verbose 2.7.4
$ rbenv global 2.7.4
$ eval "$(rbenv init -)"
```

At this point, we have a working Ruby installation. You can run `ruby --version` to verify that.

# Build Omnibus Toolchain

According to [its Github repo](https://github.com/chef/omnibus), omnibus

> Easily create full-stack installers for your project across a variety of platforms.

Omnibus can be used to create deb, rpm packages using a consistent set of tools.

Using the following commands to clone the repo and install the gems needed for building omnibus toolchain.

```
[~]$ git clone https://github.com/chef/omnibus-toolchain.git
$ cd omnibus-toolchain
$ bundle config set without 'development'
$ bundle install --path=.bundle
```

Now we can use `omnibus` to build `omnibus-toolchain`. By default, `omnibus` will write to `/opt/omnibus-toolchain` and `/var/cache/omnibus`. We need to create those directory and make sure the curernt user owns them. Alternatively, you can make those directory writable by everyone (`chmod 777`) but it is not recommended.

```
# mkdir /opt/omnibus-toolchain
# mkdir /var/cache/omnibus
# chown $USER:$USER /opt/omnibus-toolchain
# chown $USER:$USER /var/cache/omnibus
[/home/user/omnibus-toolchain]$ bundle exec omnibus build omnibus-toolchain
```

This process will take quite some time as it downloads dependencies and build everything from scratch. Once this is done, you'll find the deb package sitting in the `pkg` directory. The name encodes the date and time it was created. For example, mine is `omnibus-toolchain_2.1.15+20211021050910-1_arm64.deb`. You can keep it for future use. The content of the package is already stored in `/opt/omnibus-toolchain`. In fact, the package is built from the files in that directory. However, if you prefer a clean install, you can delete that directory and install the package.

```
# rm -rf /opt/omnibus-toolchain
# dpkg -i omnibus-toolchain_2.1.15+20211021050910-1_arm64.deb
```

# Build and Install Chef

Finally, we have all the tools ready to build Chef. Clone the Chef repo and install the necessary gems. As of now, the latest version is `17.7.20`. By default, the main branch has the latest version.

```
[~]$ git clone --depth=1 https://github.com/chef/chef.git
$ cd chef/omnibus
$ bundle install --path=.bundle
```

Similar to `omnibus-toolchain`, we need to create the directory that will be used during the build. Then we can kick off the build.

```
# mkdir /opt/chef
# chown $USER:$USER /opt/chef
$ bundle exec omnibus build chef
```

Again, this will take some time. Once finished, you'll find the deb package in `chef/omnibus/pkg/` directory, like `chef_17.7.11+20211021063545-1_arm64.deb`. Just like `omnibus-toolchain`, the files in this package already exist in `/opt/chef`. You can delete the directory and perform a clean install using the package.

Hooray! Chef is installed.

# Appendix

This article is based on [Matt Ray's blog article](https://mattray.github.io/2019/05/18/chef-15-on-arm) _Building Chef 15.0.300 for CentOS, Debian and Raspbian on 32-bit ARM_, with some modifications.

- Omitted the creation and usage of the `omnibus` user part, as I believe it is not necessary for one-off build.
- Skipped the patches as they have already been merged into the main branch.
- Use `bundle config set without 'development'` since `--without` option is deprecated.
- Added `--depth=1` to all `git clone` commands to save some time and bandwidth.
