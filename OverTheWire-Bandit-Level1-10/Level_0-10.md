## Level-by-Level Breakdown 

Level 0-10

---

# Level 0 ➜ 1

**Objective**: SSH into the Bandit game using a provided password.

**Command:**

```bash
ssh bandit0@bandit.labs.overthewire.org -p 2220
# Password: bandit0

```

Once you're logged in, you're officially in the game.

## Lets Begin

# Level 1 ➜ 2

Objective: Read the contents of a file literally named -
Command:

```bash
    cat ./-

```
The ./ tells the shell you're referring to a file in the current directory, not passing a flag.



# Level 2 ➜ 3

Objective: Read a file with spaces in its name.

Command:

```bash

cat "spaces in this filename"
```
Wrap it in quotes to treat the full name as one string.

# Level 3 ➜ 4

Objective: There's a hidden file in the inhere/ directory.

Command:

```bash

ls -al inhere
cat inhere/.hidden
```
ls -al lists hidden files. That dot before the filename is your clue.

# Level 4 ➜ 5

Objective: Find a human-readable file that:

                            * Is 1033 bytes

                            * Is not executable

                            * Is not a symlink

Command:

```bash
find inhere -type f -size 1033c ! -executable ! -name "*.symlink"
cat inhere/-file07
```
The file’s name is weird. Just use tab completion or quotes to read it.

# Level 5 ➜ 6

Objective: Find a file anywhere on the system that is:

                      *  Owned by bandit7

                      * Group is bandit6

                      * Exactly 33 bytes

Command:

```bash
find / -user bandit7 -group bandit6 -size 33c 2>/dev/null
cat /path/to/that/file
```
The 2>/dev/null part hides permission errors from cluttering your terminal.

# Level 6 ➜ 7

Objective: Password is stored somewhere in files. You need to search recursively.

Command:

```bash
find . -type f -exec grep -l 'password' {} \;
```
You're basically asking: “Hey system, which of these files contains the word password?”

# Level 7 ➜ 8

Objective: A specific line in a file says "millionth". That's your target.

Command:

```bash
grep millionth data.txt
```
Short and sweet. Let grep do the heavy lifting.

# Level 8 ➜ 9

Objective: Find the only line in the file that appears once. All others are duplicates.

Command:

```bash

sort data.txt | uniq -u
```
You have to sort it first — uniq only works on adjacent lines.

# Level 9 ➜ 10

Objective: Decode a file that’s been base64 encoded.

Command:

```bash

base64 --decode data.txt
```
You’re now dabbling in encoding/decoding — a key step in many CTF challenges.

## WhatTo See Here

The shell is your friend. Not a scary black box.

Everything in Linux is a file. Even weirdly named files(Surprise Surprise).

Commands like find, grep and cat are surgical tools.(Surgeon tools I would say)

Thinking logically and staying curious are essential hacker skills.


## What's Next?

Game	Purpose

Bandit Level 11+	More advanced file manipulations and SSH tricks

Narnia	C-based binary exploitation


## Author 

Written by [SortSec](https://github.com/sortlight)