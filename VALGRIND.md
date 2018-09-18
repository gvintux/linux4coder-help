# linux4coder help valgrind

## Description

Valgrind is a program analyze tool

## Preparations

* ensure that your program built in **build** directory

* change current working directory to **build**

* it's recommended to run `memcheck` tool with debug version of program and `callgrind` with release version


## Run

* run `valgrind --quiet --tool=memcheck --leak-check=full <myprogam>` to analyze `<myprogam>` for memory leak

* run `valgrind --quiet --callgrind-out-file=callgrind.log --tool=callgrind <myprogam>`  to analyze `<myprogam>` for time costs and bottlenecks

* run `callgrind_annotate --auto=yes --include=../src/ callgrind.log` to get interpretation of `callgrind` output
