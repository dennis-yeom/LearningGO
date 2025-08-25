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


To make a module...
1. Navigate into the desired directory.
2. Run the `go mod init [moduleName]` inside of the desired directory to mark it as a Go module.


### go build
Our hello.go program...
```
package main	//main is the entry point of the program.

import "fmt"	//import format package/library

func main(){
//indent to be fixed by `go fmt`
fmt.Println("Hello, World!")
}
```

Running `go build` gives us `hello_world.exe` which is the name we defined when we did `go mod init hellow_world`.

This is our executable which we can run using `./hello_world`.

You can also get the binary like so: `go build -o hello`


### go fmt
To fix the indent from the previous section, run the command `go fmt ./...`

`./...`  tells Go to apply the command do all files in the current directory and all subdirectories. This is Go-specific syntax.

After running `go fmt ./...`
```
package main //main is the entry point of the program.

import "fmt" //import format package/library

func main() {
	fmt.Println("Hello, World!") //indent error. to be fixed by `go fmt`.
}
```

### go vet
Changing fmt.Println in hello.go...
```
package main //main is the entry point of the program.

import "fmt" //import format package/library

func main() {
	fmt.Printf("Hello, %s!\n") //fixed indent!
}
```

Notice that there is no value assigned for the %s placeholder. This code will compile and run, but it's incorrect.

`go vet` detects for things such as this...

```
PS C:\Users\dennn\Desktop\LearningGO\01. Setting up Your Go Environment> go vet ./...
# hello_world
# [hello_world]
.\hello.go:6:2: fmt.Printf format %s reads arg #1, but call has 0 args
```

`go build` to create the new executable and run it.


## Makefiles
A script that specifies build steps. Good for making sure everyone will be able to run/compile the code.

Install Chocolately to install `make`.

```
#when running `go build`
# 1. go to vet
# 2. go to fmt
# 3. then back up.
# 4. `go build` is last.

.DEFAULT_GOAL := build	#default target for make. this runs if only `make` is run w/o an argument.

.PHONY: fmt vet build	#tells make these are not directories, but *targets* (commands).

fmt:					#`make fmt` runs this
	go fmt ./...

vet: fmt				#vet depends on fmt. make will run go fmt and then go vet.
	go vet ./...

build: vet				#build depends on vet.
	go build

```

`make` to run the Makefile.

```
PS C:\Users\dennn\Desktop\LearningGO\01. Setting up Your Go Environment> make  
go fmt ./...
go vet ./...
go build
```

## The Go Compatibility Promise
Read up at https://oreil.ly/p_NMY

They will try to keep backwards compatibility, but some commands have ended up breaking before.

## Staying Up-to-Date
Go programs compile to a standalone binary. You do not need to worry about currently deployed programs failing.

## Excercises


## Wrapping Up


