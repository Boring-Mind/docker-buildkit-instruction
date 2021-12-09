# Instructions how to set up Docker Buildkit in rootless mode

1. Install HomeBrew
```shell
# Install packages required by Brew
sudo apt-get install build-essential

# Install Brew
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Setup HomeBrew:
```shell
# Add brew to your PATH
echo 'eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)"' >> /home/username/.profile
eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)"

# Install GCC (recommended)
brew install gcc
```
[Latest instruction](https://brew.sh/)

2. Install Docker BuildKit
```shell
brew install buildkit
```
[Latest instruction](https://github.com/moby/buildkit#buildkit)

3. Start Docker Buildkit daemon in rootless mode:
Note: doesn't work
```shell
# Start daemon
rootlesskit buildkitd

# Isolate daemon/s network namespace from the hosts' one
rootlesskit --net=slirp4netns --copy-up=/etc --disable-host-loopback buildkitd
```
[Latest instruction](https://github.com/moby/buildkit/blob/master/docs/rootless.md)
