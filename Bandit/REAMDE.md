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







