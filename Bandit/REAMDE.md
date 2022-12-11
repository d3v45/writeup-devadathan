# OverTheWire
# Bandit
## Level 0
```
ssh bandit0@bandit.labs.overthewire.org -p2220
```

Pass: bandit0

**What did i learnt:-**

Understood what is **ssh**

## Bandit Level 0 → Level 1

Done it with the command cat
```
cat readme
```

**What did i learnt:-**

Learnt about cat command

cat - concatenate files and print on the standard output

pass: NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL

## Bandit Level 1 → Level 2

Used cat ./- to open a dashed filename
```
cat <-
```
```
cat ./-
```

**What did i learnt:-**

cat <- or cat ./- commands are used to open a dashed filename

Pass: rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi

## Bandit Level 2 → Level 3

```
cat spaces\ in\ this\ filename\
```
or

```
cat "spaces in this filename"
```

Pass: aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG

## Bandit Level 3 → Level 4

```
cd inhere
ls -a
cat .hidden
```
**What did i learnt:-**

ls -a gives list of all files including hidden files

Pass: 2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe

## Bandit Level 4 → Level 5

Tried to read files one bye one with using cat and ./ used because filename starting with "-"
```
cd inhere
ls
cat ./-file07
```

Pass: lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR

## Bandit Level 5 → Level 6
In question hints, they given human readable and its size

To find size we use "du" command
and to get size in bytes we use "-b"
to get size of all we use "-a"

```
ls
cd inhere
ls
ls -al * | grep -B 10 1033
cat maybehere07/.file2
```
 **What did i learnt:-**
 
 du - estimate file space usage
 
  -b, --bytes
              equivalent to '--apparent-size --block-size=1'
 

Pass: P4L4vucdmLnm8I7Vl7jG1ApGSfjYKqJU

## Bandit Level 5 → Level 6

```
find / -user bandit7 -group bandit6 -size 33c
```

after this, we get where the password is located

/var/lib/dpkg/info/bandit7.password

We want to read output with cat command

```

cat /var/lib/dpkg/info/bandit7.password
```

Pass: z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99S

## Bandit Level 7 → Level 8

 In this level first we want to read output with using cat command
 
 There are so many passwords given,
 
 In these the correct password is given next to the word millionth 
 
 so we want to use command "grep millionth"
 
 we can use pipe ( | ) to enter both command in one line
 ```
 cat data.txt | grep millionth
 ```
 **What did i learnt:-**
 
 Pipe is used to combine two or more commands
 
 Pass: TESKZC0XvTetK0S9xNwm25STk5iWrBvP
 
## Bandit Level 8 → Level 9

In question given that only line of text that occurs only once

So we need to sort and need to see the line occurs only one

we use  "sort" command  for sorting and we use "unique"  command to find line occurs only once 

with help of pipe to to make all in one line command
```
cat data.txt | sort | uniq -u
```
 **What did i learnt:-**
 Studied how and when to use "unique" command and "sort" command
Pass: EN632PlfYiZbn3PhVK3XOGSlNInNE00t
## Bandit Level 9 → Level 10
In this we want to read the file using cat command and it is few human-readable strings

So we want to find strings

Using both in one line with pipe
```
cat data.txt | strings
```
 **What did i learnt:-**
 
 "Strings" command is used to find strings
 
 Pass: G7w8LIi6J3kTb8A7j9LgrywtEUlyyp6s
 ## Bandit Level 10 → Level 11
Next passwerd contains base64 encoded data

We need to find which are base64 encoded data and we need to decode that
```
cat data.txt | base64 -d
```
Then the output will be

The password is 6zPeziLdR2RKNdNYFNb6nVCKzphlXHBM
 **What did i learnt:-**
 Learned to use "base64" command and 
 
 "-d" with that command is to decode.
 
 Pass: 6zPeziLdR2RKNdNYFNb6nVCKzphlXHBM
 ## Bandit Level 11 → Level 12
 password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions
 
 First read the file data.txt using cat command 
 ```
 cat data.txt
 ```
 got a ciphertext 
 
 "Gur cnffjbeq vf WIAOOSFzMjXXBC0KoSKBbJ8puQm5lIEi"
 
 Decoded it online with "ROT13 decoder"
 
 and got the password like given below
 
 The password is JVNBBFSmZwKKOP0XbFXOoW8chDz5yVRv
 
 Pass: JVNBBFSmZwKKOP0XbFXOoW8chDz5yVRv
 
 ## Bandit Level 12 → Level 13
 Next passwrd is stored file data.txt, which is a hexdump of a file that has been repeatedly compressed.
 
 tried 
 
```
ls
cat data.txt
```

didn't got password so we want to create a directory under /tmp
```
mkdir /tmp/newfile666
```
copy files in data.txt to the new directory named "newfile666"
```
cp data.txt /tmp/newfile666
```
Enter the directory using cd command
```
cd /tmp/newfile666
```
xxd - make a hexdump or do the reverse.
```
xxd -r data.txt data
```
file command is used to identify the type of file

we want to identify the type of file "data"

```
file data
```
Got outpu as 

data: gzip compressed data, was "data2.bin", last modified: Sat Dec  3 08:13:49 2022, max compression, from Unix, original size modulo 2^32 170795040

Understood that is a gzip compressed data 

we want to decompress it 

We need to rename it to **.gz** format to decompress it

**mv** command is used to Move or rename files
```
mv data data.gz
```
After changing **data** to **data.gz** 

Next step is to decompress

**gzip -d [file]** command used to decompress
```
gzip -d data.gz
```
Check using **file** command we got it or do we need to decompress more
```
file data
```
Output:

data: bzip2 compressed data, block size = 900k

Identified this is a bzip2 compressed data

we need to rename to **.bz2** format and decompress it
```
mv data data.bz2
bzip2 -d data.bz2
```
Check using **file** command we got it or do we need to decompress more
```
file data
```
Output:

data: gzip compressed data, was "data4.bin", last modified: Sat Dec  3 08:13:49 2022, max compression, from Unix, original size modulo 2^32 20480

Identified it is a gzip compressed data

we need to rename to **.gz** format and decompress it
```
mv data data.gz
gzip -d data.gz
```
Check using **file** command we got it or do we need to decompress more
```
file data
```
Output:

data: POSIX tar archive (GNU)

Identified it as a POSIX tar archive

tar - an archiving utility

we need to extract the file

```
tar -x -f data
file data5.bin
tar -x -f data5.bin
```
we got a file named data6.bin

Check using **file** command we got it or do we need to decompress more

```
file data6.bin
```
Output:

data6.bin: bzip2 compressed data, block size = 900k

Identified this is a bzip2 compressed data

We need to extract it

```
bzip2 -d data6.bin
```
bzip2: Can't guess original name for data6.bin -- using data6.bin.out

Check using **file** command we got it or do we need to decompress more
```
file data6.bin.out
```
Output:

data6.bin.out: POSIX tar archive (GNU)

Identified it as a POSIX tar archive

we need to extract the file
```
tar -x -f data6.bin.out
```
Got a file named **data8.bin**

Check using **file** command we got it or do we need to decompress more
```
file data8.bin
```

Output:

data8.bin: gzip compressed data, was "data9.bin", last modified: Sat Dec  3 08:13:49 2022, max compression, from Unix, original size modulo 2^32 49

Identified it is a gzip compressed data

we need to rename to **.gz** format and decompress it

```
mv data8.bin data8.gz
gzip -d data8.gz
```
Got a file named **data8**

Check using **file** command we got it or do we need to decompress more
```
file data8
```
Output:

**data8: ASCII text**

We found it as ASCII text

Read **data8** using cat command
```
cat data8
```
Output:

The password is wbWdlBxEir4CaE8LaPhauuOo6pwRmrDw

Finally got the password

All commands :- 

```
ls
cat data.txt
mkdir /tmp/newfile666
cp data.txt /tmp/newfile666
cd /tmp/newfile666
xxd -r data.txt data
file data
mv data data.gz
gzip -d data.gz
file data
mv data data.bz2
bzip2 -d data.bz2
file data
mv data data.gz
gzip -d data.gz
file data
tar -x -f data
file data5.bin
tar -x -f data5.bin
file data6.bin
bzip2 -d data6.bin
file data6.bin.out
tar -x -f data6.bin.out
file data8.bin
mv data8.bin data8.gz
gzip -d data8.gz
file data8
cat data8
```
Pass: wbWdlBxEir4CaE8LaPhauuOo6pwRmrDw

## Bandit Level 13 → Level 14
Given that the password **can only be read by user bandit14**

Got a private SSH key that can be used to log into the next level

localhost is the hostname

```
ssh bandit14@localhost -i sshkey.private -p 2220
```
Entered to bandit14

Wanted to find the password to enter bandit14

Password is stored in /etc/bandit_pass/bandit14 

We can read output using **cat** command
```
cat /etc/bandit_pass/bandit14
```
Output:

fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq

Got the password

Pass: fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq

## Bandit Level 14 → Level 15

Used **nc** command to connect with port 30000 on localhost.

The Netcat ( nc ) command is a command-line utility for reading and writing data between two computer networks.
```
nc localhost 30000
```

And gave the password of level 14
```
fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq
```
Output:

Correct!
jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt
 
Pass: jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt 

## Bandit Level 15 → Level 16
```
openssl s_client -connect localhost:30001
```
After entering to the port ,
Gave previous password
```
jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt
```
Pass: JQttfApK4SeyHwDlI9SXGR50qclOAil1

In this level i studied when to use and where to use **openssl** command and **s_client** command 

OpenSSL is a cryptography software library or toolkit that makes communication over computer networks more secure. 
 
The s_client command implements a generic SSL/TLS client which connects to a remote host using SSL/TLS . It is a very useful diagnostic tool for SSL servers.


## Bandit Level 16 → Level 17
Using nmap -p <port ranges> <target specification> command, we will perform a port scan to identify the open ports between the range of 31000 to 32000
 
```
 nmap -p 31000-32000 localhost
 ```
 the output we received for
 ```
 cat /etc/bandit_pass/bandit16 | openssl s_client -connect localhost:31790 -quiet
 ```
 Got a private key
 ```
 -----BEGIN RSA PRIVATE KEY-----
MIIEogIBAAKCAQEAvmOkuifmMg6HL2YPIOjon6iWfbp7c3jx34YkYWqUH57SUdyJ
imZzeyGC0gtZPGujUSxiJSWI/oTqexh+cAMTSMlOJf7+BrJObArnxd9Y7YT2bRPQ
Ja6Lzb558YW3FZl87ORiO+rW4LCDCNd2lUvLE/GL2GWyuKN0K5iCd5TbtJzEkQTu
DSt2mcNn4rhAL+JFr56o4T6z8WWAW18BR6yGrMq7Q/kALHYW3OekePQAzL0VUYbW
JGTi65CxbCnzc/w4+mqQyvmzpWtMAzJTzAzQxNbkR2MBGySxDLrjg0LWN6sK7wNX
x0YVztz/zbIkPjfkU1jHS+9EbVNj+D1XFOJuaQIDAQABAoIBABagpxpM1aoLWfvD
KHcj10nqcoBc4oE11aFYQwik7xfW+24pRNuDE6SFthOar69jp5RlLwD1NhPx3iBl
J9nOM8OJ0VToum43UOS8YxF8WwhXriYGnc1sskbwpXOUDc9uX4+UESzH22P29ovd
d8WErY0gPxun8pbJLmxkAtWNhpMvfe0050vk9TL5wqbu9AlbssgTcCXkMQnPw9nC
YNN6DDP2lbcBrvgT9YCNL6C+ZKufD52yOQ9qOkwFTEQpjtF4uNtJom+asvlpmS8A
vLY9r60wYSvmZhNqBUrj7lyCtXMIu1kkd4w7F77k+DjHoAXyxcUp1DGL51sOmama
+TOWWgECgYEA8JtPxP0GRJ+IQkX262jM3dEIkza8ky5moIwUqYdsx0NxHgRRhORT
8c8hAuRBb2G82so8vUHk/fur85OEfc9TncnCY2crpoqsghifKLxrLgtT+qDpfZnx
SatLdt8GfQ85yA7hnWWJ2MxF3NaeSDm75Lsm+tBbAiyc9P2jGRNtMSkCgYEAypHd
HCctNi/FwjulhttFx/rHYKhLidZDFYeiE/v45bN4yFm8x7R/b0iE7KaszX+Exdvt
SghaTdcG0Knyw1bpJVyusavPzpaJMjdJ6tcFhVAbAjm7enCIvGCSx+X3l5SiWg0A
R57hJglezIiVjv3aGwHwvlZvtszK6zV6oXFAu0ECgYAbjo46T4hyP5tJi93V5HDi
Ttiek7xRVxUl+iU7rWkGAXFpMLFteQEsRr7PJ/lemmEY5eTDAFMLy9FL2m9oQWCg
R8VdwSk8r9FGLS+9aKcV5PI/WEKlwgXinB3OhYimtiG2Cg5JCqIZFHxD6MjEGOiu
L8ktHMPvodBwNsSBULpG0QKBgBAplTfC1HOnWiMGOU3KPwYWt0O6CdTkmJOmL8Ni
blh9elyZ9FsGxsgtRBXRsqXuz7wtsQAgLHxbdLq/ZJQ7YfzOKU4ZxEnabvXnvWkU
YOdjHdSOoKvDQNWu6ucyLRAWFuISeXw9a/9p7ftpxm0TSgyvmfLF2MIAEwyzRqaM
77pBAoGAMmjmIJdjp+Ez8duyn3ieo36yrttF5NSsJLAbxFpdlc1gvtGCWW+9Cq0b
dxviW8+TFVEBl1O4f7HVm6EpTscdDxU+bCXWkfjuRb7Dy9GOtt9JPsX8MBTakzh3
vBgsyi/sN3RqRBcGU40fOoZyfAMT8s1m/uYv52O6IgeuZ/ujbjY=
-----END RSA PRIVATE KEY-----
```
 Save the key in a new folder
 ```
mkdir /tmp/name123         
cd /tmp/name123             
 ```
Using vim editor we will copy and paste the RSA private key into a file named, sshkey.private, under name123 folder
```
vim sshkey.private
```
 Paste the key in vim editor 
 Enter **:wq** to save and exit from vim editor

If we want to check by reading the key 
```
cat sshkey.private
```
 
 change the sshkey.private file’s permission using chmod command to only allow the owner (thats you) the ability to read and write access. This is done by executing chmod 400 sshkey.private command.
```
chmod 400 sshkey.private
```
 After this, next step is connecting to the port
```
sh -i sshkey.private bandit17@localhost -p2220
```
 Now we are in bandit17
 To get the password, 
```
cat /etc/bandit_pass/bandit17
```
 
 Pass: VwOSWtCA7lRKkTfbr2IDh6awj9RNZM5e
 
 ## Bandit Level 17 → Level 18
 
 
 
 
 
 
 
 
 
 
 
 






