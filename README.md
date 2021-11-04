# How I use GDB
Collection of GDB commands that I use sometimes

### Exit point of a function
Tells where a function returned.
```
(gdb) record
(gdb) fin
(gdb) reverse-step
```

### Annoying sigpipe
Sometimes my application keeps receiving this signal while I try to debug. Dont know why but this is my solution.
```
(gdb) handle SIGPIPE nostop noprint pass
```

### Saving breakpoints for future use
You can save the breakpoints of a session to load them later!
```
(gdb) save breakpoints <filename>
Saved to file 'bp'.
```
After saving you can continue your debug session normally. In this example I used _bp_ as filename. To load the breakpoints, even in another session use:
```
(gdb) source <filename>
```

### Pretty Print
Show objects and structures in a better way.
```
(gdb) set print pretty on
```

### Print complete strings
When you have a long string, the print command won't print all the characters. To solve this:
```
(gdb) set print elements 0
```

### Save what you need to a file
In Linux, I save what I always use to a file, so I don't need to type the same commands every time:
```bash
> cat ~/.gdbinit
set pretty print on
set print elements 0
```

### Optional front-end
Most of the time I use [**cgdb**](https://github.com/cgdb/cgdb). The command set is the same as GDB, and you can see the source code while you debug.
