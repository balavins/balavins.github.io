---
title: GDB commands
---

My most commonly used gdb commands

GDB for application debug
```
gdb --args ./application.bin -i inp.bin -o out.bin 
b app.cpp:154 -break
r - run
s - single step
n - next line
q
bt - backtrace
f - go to a particular frame in gdb
```

GDB for debugging a core-dump 

gdb ./app core

In gdb to dump memory locations use

```
dump binary memory result_val1.bin 0x7febef0b2040 0x7febef0bb570
https://stackoverflow.com/questions/16095948/gdb-dump-memory-save-formatted-output-into-a-file
dump binary memory result.bin 0x200000000 0x20000c350
```

Split gdb into two windows for code and debug
ctrl x + ctrl a shows code base in two windows
if messed up use ctrl + l  to reset screen


When debugging several threads, sometimes the following command is quite useful.
https://stackoverflow.com/questions/18391808/how-to-get-the-backtrace-for-all-the-threads-in-gdb  
```
thread apply all bt
t a a bt
```
if you are looking for a specific lib or crashpoint, the above could help

I have also in the past, written/helped write python programs that could parse gdb outputs automatically and investigate threads
Example:
https://interrupt.memfault.com/blog/automate-debugging-with-gdb-python-api
https://stackoverflow.com/questions/4060565/how-to-script-gdb-with-python-example-add-breakpoints-run-what-breakpoint-d
