# linux4coder help make

## Description

Make is a build tool

## Make Rules

Make rules should be placed in file **Makefile** by default

Rule consists of *target*, *requisites* and *commands* like this

```makefile
    <target>: <requisite_1> <requisite_2> ... <requisite_N>
        <command_1>
        <command_2>
        ...
        <command_N>
```
for example:

```makefile
    myprogram: main.o
        $(cc) main.o -o myprogram
    main.o: main.c
        $(cc) -c main.c
```
where:
* **myprogram**, **main.o** are targets
* **main.c**, **main.o** are requisites
* `$(cc) -c main.c` and `$(cc) main.o -o myprogram` are commands

Dependencies are resolving automatically. So, if you need to build **myprogram** which depends on **main.o** then **main.o** target will be build automatically

## Run

* run `make` where **Makefile** is located to build default target

    or

* run `make <target>` to build exactly &lt;target&gt;

## Notes

*For indentation in Makefile you need to use tabs not spaces*
