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
