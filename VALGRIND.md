# linux4coder help valgrind

## Description

Valgrind is an program analyze tool

## Preparations

* ensure that your program built in **build** directory

* change current working directory to **build**

## Run

* run `valgrind --quiet --leak-check=full <myprogam>` to analyze `<myprogam>` for memory leak

* run `valgrind --quiet --callgrind-out-file=callgrind.log --tool=callgrind <myprogam>`  to analyze `<myprogam>` for time costs and bottlenecks

* run `callgrind_annotate --auto=yes --include=../src/ callgrind.log` to get interpretation of `callgrind` output
