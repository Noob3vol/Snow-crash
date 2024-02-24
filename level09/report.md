# Level09
## Description
The level 09 user has an executable **level09** and a token file,  which user is `flag09`. The token is encrypted.

## Exemple ./level09
```bash
level09@SnowCrash:~$ ./level09 111111111
123456789
level09@SnowCrash:~$ ./level09 aaaaaaaa
abcdefgh
level09@SnowCrash:~$ ./level09 abcdefgh
acegikmo
```

## Solution
- We need to decrypt the token .<br>It seems that the crypting do a loop which add pos to the original value of the char until the end of the string.<br>We need to do the oposite to decrypt.

```c
int main(int argc, char ** argv)
{
	if (argc != 2)
	{        
		return(0);
	}    
	char *cpy = strdup(argv[1]);
	if (!cpy)
		return(0);
	for (size_t i = 0; i < strlen(argv[1]); i++)
	{
		cpy[i] -= i;
	}
	write (1, cpy , strlen(cpy));
	return (0);
}
```

- Next we compile and execute the program with token in parameter.

```bash
cc -std=c99 test.c; 
cat ~level09/token | xargs ./a.out
f3iji1ju5yuevaus41q1afiuq
```

- We found the password of `flag09`, use it to connect to `flag09` and execute `getflag`.
