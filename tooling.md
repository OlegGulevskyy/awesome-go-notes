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

```go
$ go get golang.org/dl/go.1.15.6
$ go1.15.6 download
```

Example usage
```go
go1.15.6 build
```
