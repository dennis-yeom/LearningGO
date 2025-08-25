# Chapter 1: Setting Up Your Go Environment
Follow along to set up Go and troubleshoot any issues.


## Installing the Go Tools
Download Go here: https://go.dev/dl

### Troubleshooting Your Go Installation
- Check installation with `go version`
- If you receive an error, you may not have Go installed in your executable path.
- On macOS/Unix-like systems, try `which go`.

### Go Tooling
- Compiler: `go build`
- Code Formatter: `go fmt`
- Dependency Manager: `go mod`
- Test Runner: `go test`
- Mistake Finder: `go vet`


## Your First Go Program 
Intro to different parts of a Go program. 

### Making a Go Module
A Go project is called a ***module***. A module contains not just cource code, but the exact specifications required for dependencies. Every module has a ***go.mod*** file in its root directory. The ***go.mod*** file is created after running `go mod init`.

You should not edit the ***go.mod*** file directly. Instead, use the following commands...
- `go get`: Used to add/update a dependency in your module.
- `go mod tidy`: Adds dependencies the code uses; removes unused dependencies.



1. Navigate into the desired directory.
2. Run the `go mod init [moduleName]` inside of the desired directory to mark it as a Go module.
2. 


### go build


### go fmt


### go vet



## Makefiles


## The Go Compatibility Promise


## Staying Up-to-Date


## Excercises


## Wrapping Up


