# Level00

After connecting to the vm using login `level00:level00`

Home directory being empty we will search for any file belonging to the user we want to connect *flag00*

![find flag00 file](level00_1 "find_flag00_file")
>`find / -user flag00 2> /dev/null`

Opening the *john* file we found we got a charactere string: *cdiiddwpgswtgt*

Testing the string as `flag00` passwd end in a failure so it is most probably crypted

Using a code recognition tools we have an hint that it is probably a rot or a ceasar encryption

![Encryption recognition image](level00_3.png "Rot but not rotting")

using the same tools to decode string as a rot we get the string `nottohardhere` as a result

Trying it as `flag00` get us access to the account *cheers*

![x24ti5gi3x0ol2eh4esiuxias](level00_2.png "Easy peasy")
