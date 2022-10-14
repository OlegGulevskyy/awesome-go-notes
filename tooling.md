# Makefile

```
.DEFAULT_GOAL := build

fmt:
        go fmt ./...
.PHONY:fmt

lint: fmt
        golint ./...
.PHONY:lint

vet: fmt
        go vet ./...
.PHONY:vet

build: vet
        go build hello.go
.PHONY:build
```


# Compatibility

Despite these backward compatibility guarantees, bugs do happen, so it’s natural to want to make sure that a new release doesn’t break your programs. One option is to install a secondary Go environment. For example, if you are currently running version 1.15.2 and wanted to try out version 1.15.6, you would use the following commands:

```shell
$ go get golang.org/dl/go.1.15.6
$ go1.15.6 download
```

Example usage
```shell
go1.15.6 build
```

Once you have validated that your code works, you can delete the secondary environment by finding its GOROOT, deleting it, and then deleting its binary from your $GOPATH/bin directory. Here’s how to do that on Mac OS, Linux, and BSD:

```shell
$ go1.15.6 env GOROOT
/Users/gobook/sdk/go1.15.6
$ rm -rf $(go1.15.6 env GOROOT)
$ rm $(go env GOPATH)/bin/go1.15.6
```
When you are ready to update the Go development tools installed on your computer, Mac and Windows users have the easiest path. Those who installed with brew or chocolatey can use those tools to update. Those who used the installers on https://golang.org/dl can download the latest installer, which removes the old version when it installs the new one.

Linux and BSD users need to download the latest version, move the old version to a backup directory, expand the new version, and then delete the old version:

```shell
$ mv /usr/local/go /usr/local/old-go
$ tar -C /usr/local -xzf go1.15.2.linux-amd64.tar.gz
$ rm -rf /usr/local/old-go
```

