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






