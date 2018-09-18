# linux4coder help gdb

## Description

GDB is a debbugger

## Run
* program should be compiled with `-g` flag to add debug info

* run `gdb <program>`

* set a breakpoint to stop program execution on exact line using commands

    * `break <line_number>`

    * `break [file_name]:<line_number>`

    * `break [file_name]:<func_name>`

* use command `run [args]` to start running the program

* use command `print <variable>` to print current value of the `<variable>`

There are three kind of `gdb` operations you can choose when the program stops at a break point. They are continuing until the next break point, stepping in, or stepping over the next program lines.

* `c` or `continue`: debugger will continue executing until the next break point

* `n` or `next`: debugger will execute the next line as single instruction

* `s` or `step`: same as next, but does not treats function as a single instruction, instead goes into the function and executes it line by line.

Use following shortcuts for most of the frequent `gdb` operations:

* `l` – list
* `p` – print
* `c` – continue
* `s` – step
* <kbd>ENTER</kbd> would execute the previously executed command again

Miscellaneous gdb commands:

* `l` command: use gdb command l or list to print the source code in the debug mode

    Use `l <line-number>` to view a specific line number (or) `l <function>` to view a specific function.
* `bt: backtrack` – print backtrace of all stack frames, or innermost COUNT frames

* `help` – view help for a particular `gdb` topic `help TOPICNAME`

* `quit` – exit from the gdb debugger

You can also run `gdb` in [TUI](https://sourceware.org/gdb/onlinedocs/gdb/TUI.html) (Text User Interface) mode
