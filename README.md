# IAB Protobuff Spec for AdCOM (WIP)

# Comments
* Where a field is an array, the name was pluralized.
* Where the spec dictates one of several fields be populated, the "oneof" label is used to enforce this.
* Where the spec recommends that only of several fields be used, the "oneof" label is used to enforce this.
* ~~Where an int is supposed to be from a list, I'm going to switch to an ENUM and enforce this (todo).~~

# Docs
Docs can be generated by invoking `make docs`. This uses the [protoc-gen-doc|https://github.com/pseudomuto/protoc-gen-doc] tool. Unfortunately, the tool doesn't support objects nested deeper than two levels.

# Developing
When iterating on the protobuff definitions, you can run `make watch` and it will run the doc generator whenever the file is saved. This is useful for checking the validity of the protobuff definitions and also for generating docs (works well with Marked 2).

## Dependencies
The Makefile provides targets that depend on the following tools being installed:
* golang
* protoc - for generating go and java bindings
* prototools - for running a linter and for formatting
* docker - for generating docs

## Makefile Targets

```compile```
Builds the Golang and Java bindings. Useful for making sure the file is valid and for seeing if the generated code makes sense.

```fmt```
Runs the prototools formatter on the protobuff files.

```check```
Runs the prototools linter.

```clean```
Deletes the code generated by the ```compile``` target.

```docs```
Generates a README.md in the docs/ subdirectory.

```watch```
Looks for updates to the protofiles and rebuilds the docs.
