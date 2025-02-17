# Hack - usage

If you want to have support for **json array syntax** in `docker run --entrypoint`. Use a patched binary.

Install - (mac/linux)
```
curl -Lo /usr/local/bin/docker-hack https://github.com/lalyos/cli-1/releases/download/hack/docker-$(uname)
chmod +x /usr/local/bin/docker-hack
alias docker=/usr/local/bin/docker-hack
```

usage:
```
$ docker run --entrypoint '["sh","-c","echo look ma entrypoint as an array"]' alpine

look ma entrypoint as an array
```


This is the commit: [3 lines change](
https://github.com/lalyos/cli-1/commit/284534fd03fd15431cd54597ded9ca9c843f67f8 )
# Hack - background

I was wondering if its possible to use **json array syntax** in `docker run --entrypoint ' alpine` the same way as `ENTRYPOINT` in a Dockerfile.

right now it's not possible
```
$ docker run --entrypoint '["sh","-c","echo ok"]' alpine

docker: Error response from daemon: failed to create task for container: failed to create shim task: OCI runtime create failed: runc create failed: unable to start container process: exec: "[\"sh\",\"-c\",\"echo ok\"]": executable file not found in $PATH: unknown.
```


# Docker CLI

[![PkgGoDev](https://pkg.go.dev/badge/github.com/docker/cli)](https://pkg.go.dev/github.com/docker/cli)
[![Build Status](https://img.shields.io/github/actions/workflow/status/docker/cli/build.yml?branch=master&label=build&logo=github)](https://github.com/docker/cli/actions?query=workflow%3Abuild)
[![Test Status](https://img.shields.io/github/actions/workflow/status/docker/cli/test.yml?branch=master&label=test&logo=github)](https://github.com/docker/cli/actions?query=workflow%3Atest)
[![Go Report Card](https://goreportcard.com/badge/github.com/docker/cli)](https://goreportcard.com/report/github.com/docker/cli)
[![OpenSSF Scorecard](https://api.scorecard.dev/projects/github.com/docker/cli/badge)](https://scorecard.dev/viewer/?uri=github.com/docker/cli)
[![Codecov](https://img.shields.io/codecov/c/github/docker/cli?logo=codecov)](https://codecov.io/gh/docker/cli)

## About

This repository is the home of the Docker CLI.

## Development

`docker/cli` is developed using Docker.

Build CLI from source:

```shell
docker buildx bake
```

Build binaries for all supported platforms:

```shell
docker buildx bake cross
```

Build for a specific platform:

```shell
docker buildx bake --set binary.platform=linux/arm64 
```

Build dynamic binary for glibc or musl:

```shell
USE_GLIBC=1 docker buildx bake dynbinary 
```

Run all linting:

```shell
docker buildx bake lint shellcheck
```

Run test:

```shell
docker buildx bake test
```

List all the available targets:

```shell
make help
```

### In-container development environment

Start an interactive development environment:

```shell
make -f docker.Makefile shell
```

## Legal

*Brought to you courtesy of our legal counsel. For more context,
see the [NOTICE](https://github.com/docker/cli/blob/master/NOTICE) document in this repo.*

Use and transfer of Docker may be subject to certain restrictions by the
United States and other governments.

It is your responsibility to ensure that your use and/or transfer does not
violate applicable laws.

For more information, see https://www.bis.doc.gov

## Licensing

docker/cli is licensed under the Apache License, Version 2.0. See
[LICENSE](https://github.com/docker/docker/blob/master/LICENSE) for the full
license text.
