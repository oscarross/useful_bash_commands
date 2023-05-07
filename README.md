# BASH
### man 
- format and display the on-line manual pages

`man [command] #if you are lost, just RTFM!`

### whoami 
- display effective user id

`whoami #prints the current user's name`

### echo 
- write arguments to the standard output

`echo "[text]" #prints out text`

### pwd 
- return working directory name

`pwd #prints the current directory`

### ls 
- list directory contents

`ls #lists the contents of the current directory`

`ls -la #lists all the files in a longer format`

`ls -lS #lists all the files sorted by size`

`ls D* # „show only files that start with “D” (Desktop, Documents, etc)”`

`ls *.{txt,xml,md}`

List the five most recently modified files
`ls -t | head -n 5`


### cd 
- change directory

`cd [directory] #moves to a given directory like "/Users/tib/"`

`cd ~ #moves to home directory`

`cd .. #moves up a directory`

### mkdir 
- make directories

`mkdir [directory] #creates a directory`

`mkdir -p [dir1/dir2/dir3] #creates the whole directory structure`

### cp 
- copy files

`cp [source] [destination] #copies the source into the destination`

`cp -R somedirectory nameofcopy #copy whole directory`

### mv 
- move files

`mv [source] [destination] #moves the source into the destination`

### ln 
- make links

`ln [source] [destination] #creates a link from the source to the destination`

### rm 
- remove directory entries

`rm [file] #removes the given file`

`rm -r [directory] #removes the given file`

### chmod 
- change file modes or Access Control Lists

`chmod 644 [file] #changes file permissions`

`chmod -r 644 [directory] #same, but recursively`

### chown 
- change file owner and group

`chown tib:staff [file] #changes owner & group`

`chown -r tib:staff [directory] #same but recursively`

### which 
- locate a program file in the user's path

`which [command] #looks for a command, if found prints location`

### touch 
- change file access and modification times

`touch [file] #creates the file or updates it's appropriate times`

### sips 
- scriptable image processing system

`sips -Z [size] [image] #scale an image to a max size`

### alias 
- creates an alias

`alias la='ls -la' #from now you can use la as a shortcut`

### export 
- exports a variable

`export [name]=[value] #later on you can assess it by using $name`

# Last parameter - $_ vs !$

`$_` is substitued by the shell with the parameter from the last command

```
git branch -d branch-name
git push --delete remote-name $_
```

When hitting enter on a command with `$!` the shell will not execute it, but prompt the command again, with the last parameter used in place of `!$`

```
$ ls ~/Desktop
$ ls -a !$
$ ls -a ~/Desktop
```

# Fix typo

```
ls *.txs

no matches found: *.txs

^txs^txt
ls *.txt
```

# Print file

### cat 
- concatenate and print files

`cat [file] #prints out the contents of a file`

### less
`less -NM filename.txt`

|Character|What it's doing|
|---|:---|
|`-N`|show numbers|
|`-M`|show metrics|

-  find "the" 
`less +/the filename.txt`

### head
`head filename.txt #Print the first 10 lines of file`

### tail
`tail -n 5 filename.txt #Print the final 5 lines of file`

# Counting lines and words

### wc 
- prints count of lines, words and bytes from file

`wc [file]`

|Character|What it's doing|
|---|:---|
|`-c`|the number of bytes|
|`-l`|the number of lines|
|`-m`|the number of characters|
|`-w`|the number of words|

# Find

### Find and move files to folder
- `find . -name "*video*.mp4" -print0 | xargs -0 -I {} mv {} new_folder`

- `find . -name "*.java" -exec grep -n -H "new .*Db.* {} \;`

- `find . -name "*.zip" -size +1G`

- `find . -name "*.java" -not -regex ".*Db\.java -exec grep -n -H "new .*Db" {} \;`

- `find . -iname "*.txt" -exec cat {} \;`

Find all "....Db.java" 
-  `find . -regex ".*Db\.java` 

Find any file modified in the last 24 hours 
- `find . -type f -mtime 0` 

Count markdouwn files
- `find . -iname "*.md" | wc -l`

|Character|What it's doing|
|---|:---|
|find|execute the `find` command|
|`.`|from the current directory|
|`-name`|match the name of "*.java"|
|`-iname`|like name, but case insensitive|
|`-size`|size criteria|
|`-exec`|will pass found filename as a parameter|
|`-n`|show line numbers of the matches|
|`-H`|show filenames of the matches|
|`"new .*Db.*"`|all files with any numbers of characters, followed by the letters Db, then followed by any characters|
|`{}`|placeholder for the filename found by `find`|
|`\;`|Terminate the command after `-exec`|

# Searching for text with grep

### grep 
- file pattern searcher

`ls -la | grep [term] #search for a folder name (term) in a directory list`

`cat test.txt | grep [term] #search for a term in a file` 

|Character|What it's doing|
|---|:---|
|`--color`|color results|
|`-r`|recursive search|
|`-i`|ignore letter case|
|`-l`|prints only matching filenames|
|`-n`|prints line number|

# Sorting and de-duping

- `sort filed.txt | uniq`

- `sort file1 file1 file2 | uniq -u`
If you combine this with the `-u` parameter to uniq, which outputs lines that exist only once.

# Search your history for a specific command

- `history | grep "command"`

# Repeat a command with root privileges

- `sudo !!`

# Measure time

- `time command`

# Share files by python 

- `python -m SimpleHTTPServer`

# Working with remote servers

`ssh-keygen -t rsa -b 4096 -C "your_email@example.com" # genertes a new key`

### ssh 
- OpenSSH SSH client (remote login program)

`ssh [server] -p [port] #logs in to a remote server`

### scp
- upload file to server
`scp filename.zip`

### sftp 
- secure file transfer program

`sftp [server] #logs in to the server (use help for more)`

After `sftp` you can upload file `put filename.zip` or download file `get filename.zip`

# Tricks
### Download website

`wget --mirror --convert-links --adjust-extension --page-requisites --no-parent http://example.org`

Alternatively, the command above may be shortened:

`wget -mkEpnp http://example.org`

# Regex

### For testing regex 
https://regex101.com/

### Characters
|Pattern|What it's doing|
|---|:---|
|`[pr]at`| A single charcter of p or r |
|`[a-z]at`| A character in the range: a-z|
|`[^a-z]at`| A character not in the range: a-z| 
|`[A-Za-z]at`| A character in the range: a-z or A-Z|
|`a?`| Zero or one of a |
|`a*`| Zero or more of a |
|`a+`| One or more of a |
|`a{3}`| Exactly 3 of a |
|`a{3,}`| 3 or more of a |
|`a{3,6}`| Beetween 3 and 6 of a |
|`.`| Any single character|
|`^`|Start of string|
|`$`|End of string|

### Multiline mode
`m` modifier: multi line. Causes `^` and `$` to match the begin/end of each line (not only begin/end of string)
- Swift `.AnchorsMatchLines`

### Grouping
"April 25h" or "Apr 25"
- `Apr(il)? \d\d(th)?`

"My name is Pat Adams" or "My name is XYZ lastname"
- `My name in (XYZ|Pat) \w+`

Find all quetes 
- `"[^"]+"`

### Non matching group

```
My favorite color is blue
My favorite colour is green
```
- `My favorite (?:color|colour) is (.*)`
    - blue
    - green


### Backreference
Find all "Testing <B>bold</B> text"
- `<([A-Z][A-Z0-9]?)>[\w ]+</\1>`