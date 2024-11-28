prepared by #MAliGhafoori , #SMostafaSarvi 

## Terminal Basics
### Address and Files
#### File name structure
A file contains two part (`name.ext`) first part is the name of that file and second part is its file format.
	such as: `background.png` or `fibonacci.cpp` etc.

#### Address structure
To find a file or directory in our computer we must use addresses. An address in computer contains of two parts (`<Letter>:\path` ) 
1. A letter that help us to specify our drive such as `C:\`
2. A direction to file and folders like `\cygwin64\bin`

and finally our address becomes like this `C:\cygwin64\bin`
#### Executable formats
We also have some file formats that OS knows how to execute theme.
	In Windows there are several formats like: `.exe` and `.js`.

when execute theme like below; the OS runs it and then show you the result of your file like though: 
```powershell
PS C:\> .\myApp.exe
Hello World
```
as you can see you should write a `.\` before your file to execute it.
### Basic flags
There are some flags that most of programs have it, like:
##### `--help` | `-h` | `\h`
These flags shows you a guide of what you can do with that app, e.g.:
```powershell
PS C:\> winget --help
```
##### `--version` `-v` `\v`
And also these flags shows you version of your installed app. e.g.
```powershell
PS C:\> gcc --version
```

**note :** usually for multi alphabets flags we use `--` and for single alphabet we use `-` 
for example : `--install` `-i`
### Operators and Symbols
there are some operators and symbols in terminal that help us in several things
#### `*` Symbol
Means all of some thing one example is in addresses
	e.g. `C:\cygwin64\*` mean everything are in `C:\cygwin` folder

#### `&&` Operator
This operator uses when you want to run two or more commands at once, and all have successfully run like:
```powershell
PS C:\> g++ ./hello_world.cpp && ./a.exe
```
it means the first command returns error others will not run properly.

#### `||` Operator
This operator uses when you want to run two or more commands at once, and all doesn't need to run successfully. e.g.
```powershell
PS C:\> command1 || command2
```

#### `|` Operator
This operator gives the output of first command to input of next command
```powershell
PS C:\> command1 | command2
```



### Terminal Management
#### Basic shortcuts
#### Clean up terminal
You can use `clear` or `cls` command to clean up your terminal.
#### Exit terminal

to close your terminal you can use this command.

```powershell
PS C:\> exit
```

#### History of terminal
##### Get history
You can use `Get-History` command gets you the list of commands you entered.
```powershell
PS C:\> Get-History
```

You can search your history by passing the result of `Get-History` to the `Select-String`.
```powershell
PS C:\> Get-History | Select-String -Pattern "g++"
```

By default, the `Get-History` only shows the 32 most recent history entries. If you want to view or search a larger number of history entries, use the `-Count` flag to specify the count of entries.
```powershell
PS C:\> Get-History -Count 1000

PS C:\> Get-History -Count 1000 | Select-String -Pattern "Example"
```

note: you can also use `history` command to get that.
##### Clear history
You can clean up the history by below command.
```
PS C:\> Clear-History
```

#### Variables
You can set variable to use later like below
```powershell
PS C:\> helloWorld = "Hello World"
```
## File and Folders management

### Change directory
`cd` changes working drive and directory. You can use this command to navigate into your working directories.
for example :
```powershell
PS C:\> cd Q:\MyDir
PS Q:\MyDir> cd MySubDir
PS Q:\MyDir\MySubDir>
```
### List
You can easily list your files and directories in you working directory using `ls` and `dir` command.
```powershell
PS C:\> ls
```
### Tree
The `tree` command is a tool for displaying the hierarchy of directories and files the basic usage only shows folders:

```powershell
PS C:\> tree

PS C:\> tree /f # for displaying files 
```

### Print working directory
The `pwd` command is used to display the current working directory.
```powershell
PS C:\> pwd
```
### Move and Rename
You can use `mv` command to move or rename your files and directories.

rename items:
```powershell
PS C:\myfolder\> mv myfile.txt myNewNameFile.txt # rename myfile.txt to myNewNameFile.txt

PS C:\myfolder\> mv myfile.txt C:\myNewPath\myNewNameFile.txt
```

### Copy
You can copy your files and directories by using `cp` and `copy` command. e.g.
```powershell
PS C:\> cp C:\data\file1.txt D:\backup\file2.txt

PS C:\> copy c:\data\file1.doc D:\backup\file2.doc
```

### Make directory
You can make directories with `mkdir` command.

```powershell
PS C:\> mkdir helloworld # create helloworld directory
```
### Remove
You can use `rm` or `del` command for deleting file and folders:
```powershell
PS C:\> rm myfile.txt # delete myfile.txt

PS C:\> del myfile.txt # delete myfile.txt

PS C:\> rm *.txt # delete everyfile with .txt extension
```

the last one delete all of your files with `.txt` file extension.

### Show and Concatenate
You can use `cat` command to show your file content or append one to other one:
```powershell
PS C:\> cat file.txt # read content of file.txt

PS C:\> cat file2.txt >> file1.txt # append file2.txt to end of file1.txt
```

### Difference
The `diff` Command is used to compare two text content, and identifies differences between them.
```powershell
PS C:\> diff file1.txt file2.txt # difference of file1.txt and file2.txt
```
### Print
The `echo` command uses to print a string or variable or put a string in a file:
```powershell
PS C:\> echo "Hello World"

PS C:\> echo $helloWorld

PS C:\> echo $helloWorld > file.txt # ignore content of file.txt and write to it

PS C:\> echo $helloWorld >> file.txt # append to file.txt
```

**note**: the difference between `>` (one shift) and `>>` (double shift) operations is the one shift will overwrites your file and delete the previous data in your file but double shift will append the string at the end of your file.
## Internet
You can also use internet in terminal.
### Check Connection

To get latency of your Internet and check your connection. and also you can limit the count of retries you can use `-c` flag.
```powershell
PS C:\> ping google.com # check if google is accessible

PS C:\> ping google.com -c 4
```
### Get content from internet

one of the usages of curl command is downloading files from links. also you can use `-o` flag to specify output file name and 
```powershell
PS C:\> curl https://cygwin.com/setup-x86_64.exe

PS C:\> curl https://cygwin.com/setup-x86_64.exe -o cygwin-setup.exe
```
### Managing Apps

`winget` is a package manager for Windows that you can install actually Microsoft Store apps from it.  You can use `winget` to update or install and uninstall your apps.

```powershell
PS C:\> winget install vscode # install visual studio code

PS C:\> winget upgrade # update every package need to be updated

PS C:\> winget uninstall vscode # uninstall visual studio code
```
