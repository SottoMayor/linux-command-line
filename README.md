# Personal Linux Command Line Docs - Bash

## Basic Informations

### Commands

* A **Full Command** consists of:  
`Command + Option(s) + Argument(s)`

* The most important part of a Full Command is the **Command** itself. Options and Arguments complement it.   
`ls` → Full Command generated by a Command.   
`ls -l -a` → Full Command generated by a Command + Options.   

* Below, these three are equivalent, and in the 2nd and 3rd cases, the order doesn't matter:  
`ls -l -a` = `ls -la` = `ls -al`   

From now on, let's refer to a 'Full Command' simply as 'Command', since there is no risk of confusion.

### Terminal

* **Home directory**: Since we opened the Terminal and the `~` is displayed on the screen, we are in the home directory.

## Write commands in a shell at the prompt

`ls`

`ls -l`

`ls -al`

`clear` -> clear the terminal

## Finding help for commands

**`man [command]`** -> `man ls`   
If we press `/`and enter what behavior we want to get, it tries to find in the list of options   
`man ls [Enter] /comma separed [Enter] it should find if the search term matchs with any option description` 

**`[command] --help`** -> `ls --help`

**`apropos [supposed command]`** -> `apropos list`   
**`apropos "[what the command suppose to do]"`** -> using double quotes we can get an exactly match


## TAB (key) completion

1. completes a file or folder name   
2. makes guesses
   
`ls -l De` followed by the Tab key

`ls -l Do` followed by the Tab key twice

`ls -l Doc` followed by the Tab key

`a` followed by the Tab key

## Helpful keyboard shortcuts

| key combination | result |
|-----------------|---------|
| CRTL + A | Move to beginning of line| 
| CRTL + E | Move to end of line|
| arrows | Move letter by letter|
| CRTL + -> | Move left one word | 
| CRTL + <- | Move right one word |
| CRTL + U | Delete from cursor to line start |
| CRTL + K | Delete from cursor to line end |
| CRTL + SHIFT + C | Copy |
| CRTL + SHIFT + V | Paste |
| (up + down) arrow | courses previous commands |
| CRTL + R | Search command history |
| CRTL + C | Cancel command |



## File system

1. Absolute path: starts with `/`for the file system root.
2. Relative path: does not.

**`file [document]`** -> Determinates the file type

**`stat [document]`** -> display the file or file system status

## Navigating the file system

**`cd`** -> Change Directory
**`pwd`** -> Print Working Directory

Go to Document folder and print the current working directory:
`cd Documents/` 
`pwd`

Using `cd`with directories with blanks:   
1. Invalid command
`cd Exercise Files`   
2. Valid commands possibilities:
2.1: Using double quotes   
    `cd "Exercise Files"`
2.2: Using scape (commom usage)
   `cd Exercise\ Files`

Listen files recursively:   
`ls -R departments/`   

Navigation between directories:  
1. `cd departments/hr/policies` -> go to `departments/hr/policies` directory   
2. `cd ..` -> up one level = `departments/hr`   
3. `cd ..` -> up (more) one level = `departments`   
4. `cd hr/policies` -> down two levels in a row = `departments/hr/policies`   
5. `cd ../../finance/documents` -> down two levels in a row, enter in finance after documents = `departments/finance/documents`   
6. `cd -` -> Back and forth between the previous and current directories   
7. `cd` -> back to the home directory   

## ls command, one of the most useful commands

`ls`

`ls --color=always` -> helpful to represent differents aspects of files

`ls -l` -> use a long listing format (see metadata)

`ls -lh` -> see metadata in human readable way, helpful to verify file sizes.

## Create and remove directories

Suppose a pre-existing `departments`folder...  

1. **Create**

- `mkdir newfolder` -> creates a new folder `newfolder`    

- `mkdir departments/customerservice` -> inside `departments` creates the `customerservice`

- `mkdir departments/customerservice/documents departments/customerservice/cases departments/customerservice/awards` -> creates more than 1 folder at once

- `mkdir -p departments/legal/contracts` -> With the `-p`, creates a folder and parent folder at once

2. **Remove**

- `rmdir departments/legal/contracts/` -> Removes folders. This removal is only allowed if the folder is empty.

- `rmdir departments/legal/` -> removes the `legal` folder


## 03_06 - Copy, move, and delete files and directories

`cp poems.txt poems2.txt`

`ls`

`cp simple_data.txt departments/hr/employee\ info/`

`ls departments/hr/employee\ info/`

`mv poems2.txt departments/marketing`

`ls departments/marketing/`

`ls`

`mv departments/marketing/poems2.txt departments/marketing/literature.txt`

`ls departments/marketing/`

`mv departments/marketing/literature.txt .`

`ls`

`ls`

`mv *.txt departments/marketing/`

`ls departments/marketing/`

`mv departments/marketing/* .`

`ls`

`rm literature.txt`

`ls`

`cp poems.txt poems3.txt`

`cp poems.txt poems4.txt`

`ls`

`rm poems?.txt`

`ls`

`rm departments/customerservice/`

`rm -r departments/customerservice/`

## 03_07 - Find files from the command line

`find . -name "poe*"`

`find . -name "do*"`

`find . -name "d*"`

`find . -name "*d*"`

`find ~/Documents -name "*d*"`

## 03_08 - Understand user roles and sudo

`ls /root`

`sudo ls /root`

`sudo ls /root`

`sudo -k`

`sudo ls /root`

`sudo -s`

`exit`

## 03_10 - Modify file permissions

`ls`

`./test.sh`

`ls -l test.sh`

`stat test.sh`

`chmod 644 test.sh` followed by Ctrl+C

`chmod -x test.sh`

`./test.sh`

`bash test.sh`

`cat test.sh`

`chmod u-r test.sh`

`chmod 244 test.sh` followed by Ctrl+C

`cat test.sh`

`chmod 755 test.sh`

`./test.sh`

`cat test.sh`

`touch newfile`

`stat newfile`

`ls -l`

`nano test.sh`

`sudo chown root test.sh`

`nano test.sh`

`ls -l test.sh`

`sudo chown [username] test.sh` (replace `[username]` with your user name)

## 03_11 - Create hard and symbolic links

`ln -s poems.txt writing.txt`

`ls -l`

`cat writing.txt`

`ln poems.txt words.txt`

`ls -l`

## 04_02 - Use pipes to connect commands together

`echo "Hello"`

`echo "Hello" | wc`

`echo "Hello world from the command line" | wc`

## 04_03 - View text files with cat, head, tail, and less

`cat poems.txt`

`head poems.txt`

`head -n5 poems.txt`

`tail -n3 poems.txt`

`cat poems.txt | cat -n | tail -n5`

`cat poems.txt | tail -n5 | cat -n`

`less poems.txt`

`cat poems.txt | less`

## 04_04 - Search for text in files and streams with grep

`grep "the" poems.txt`

`grep -n "the" poems.txt`

`grep -n "The" poems.txt`

`grep -in "The" poems.txt`

`grep -vi "the" poems.txt``grep -E "\w{6.}" poems.txt`

## 04_05 - Manipulate text with awk, sed, and sort

`cat simple_data.txt`

`awk '{print $2}' simple_data.txt`

`awk '{print $2 "\t" $1}' simple_data.txt`

`awk '{print $2 "\t" $1}' simple_data.txt | sort -n`

`cat simple_data.txt`

`sort simple_data.txt`

`sort -k2 simple_data.txt`

`cat dupes.txt`

`sort -u dupes.txt`

## 04_06 - Edit text with Vim

`vi`

`vi poems.txt`

## 04_07 - Edit text with nano

`nano`

`nano poems.txt`

## 04_08 - Working with tar and zip archives

`cd ..`

`tar -cvf myfiles.tar Exercise\ Files/`

`ls -l`

`tar -caf myfiles.tar.gz Exercise\ Files/`

`tar -caf myfiles.tar.bz2 Exercise\ Files/`

`ls -lh`

`mkdir unpack1`

`mv myfiles.tar.bz2 unpack1/`

`cd unpack1/`

`tar -xf myfiles.tar.bz2`

`ls -l`

`cd Exercise\ Files`

`ls`

`cd ~/Documents/`

`mkdir unpack2`

`tar -xf myfiles.tar.gz -C unpack2`

`ls unpack2`

`zip -r exfiles.zip Exercise\ Files/`

`ls -lh`

`mkdir unpack3`

`mv exfiles.zip unpack3`

`cd unpack3`

`unzip exfiles.zip`

`ls -l`

`cd ..`

`mkdir unpack4`

`unzip unpack3/exfiles.zip -d unpack4`

`ls -l unpack4`

## 04_11 - Output redirection

`cd Exercise\ Files`

`ls`

`ls 1> filelist.txt`

`cat filelist.txt`

`ls > filelist2.txt`

`cat filelist2.txt`

`ls notreal`

`ls notreal > filelist3.txt`

`ls notreal 2> filelist4.txt`

`cat filelist4.txt`

`>filelist4.txt`

`cat filelist4.txt`

`ls > filelist5.txt`

`echo "some appended text" >> filelist5.txt`

`cat filelist5.txt`

## 04_12 - Exploring environment variables and PATH

`env`

`echo $PATH`

`which ls`

`which less`

`ls -a`

`nano ~/.bash_profile`

## 05_01 - Find information about your Linux distribution

`ls -l /etc/*release`

`cat /etc/lsb-release`

`cat /etc/os-release`

`cat /etc/*release`

`uname -a`

`uname -r`

## 05_02 - Find system hardware and disk information

`free -h`

`cat /proc/cpuinfo`

`lscpu`

`df -h`

`sudo du -hd1 /`

`sudo lshw | less`

`ip a`

## 05_03 - Install and update software with a package manager

`apt search tree`

`apt show tree`

`tree`

`sudo apt update`

`sudo apt install tree`

`tree`

`man tree`

`sudo apt update`

`sudo apt upgrade`
