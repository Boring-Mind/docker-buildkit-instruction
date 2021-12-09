# Instructions how to set up Docker Buildkit in rootless mode

1. Install HomeBrew
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
[Latest instruction](https://brew.sh/)

2. Install Docker BuildKit
```bash
brew install buildkit
```
[Latest instruction](https://github.com/moby/buildkit#buildkit)

3. Start Docker Buildkit daemon in rootless mode:
```bash
# Start daemon
rootlesskit buildkitd

# Isolate daemon/s network namespace from the hosts' one
rootlesskit --net=slirp4netns --copy-up=/etc --disable-host-loopback buildkitd
```
[Latest instruction](https://github.com/moby/buildkit/blob/master/docs/rootless.md)
