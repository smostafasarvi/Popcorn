prepared by #MAliGhafoori  

## Address structure
 In Windows files and directories have an address like this :
 `<Letter>:\path\to\file
 `
 for example :
 `C:\user\username\Desktop`

However in unix base systems address like this
`/path/to/file`

for example :
`/home/username/Desktop`

## Executable formats
`.exe` `.cmd` `.bat` `.com` `.vbs` `.vbe` `.js` `.jse` `.wsf` `.wsh` `.msc`

to execute that formats in your terminal you can run this command for example :
```shell
PS C:\> .\myApp.exe
```

as you can see you should write a .\ before your file.

## Basic flags

##### `--help` `-h` `\h`
this flag shows a guide menu for application.
```shell
PS C:\> winget --help
```
##### `--version` `-v` `\v`
this flag shows version of your installed application.

for example :
```shell
PS C:\> gcc --version
```

**`note` :** usually for multi alphabets flag we use `--` and for single alphabet we use `-` 
for example : `--install` `-i`
## Symbols and operators
there is some symbols and operators.

`*` all of folders and files with all of formats.

`&&` this operator uses for run two or more command at one time.

```shell
PS C:\> command1 && command2
```

`||` this operator uses for run two command but the difference between this and `&&` is if one command failed to run the another command will runs successfully.
```shell
PS C:\> command1 || command2
```

`|` this operator gives the output of first command to input of next command
```shell
PS C:\> command1 | command2
```
## Terminal Management

### `cls` & `clear` Command

You can use `cls` command to clear inputs and outputs of your terminal.

### `Get-History` Command

The `Get-History` cmdlet gets the session history, that is, the list of commands entered during the current session.

You can search your history by piping the resulting output to the `Select-String` cmdlet and specifying the text you want to search for. Replace "Example" in the cmdlet below with the text you want to search for:

```bash
PS C:\> Get-History |  Select-String -Pattern "Example"
```

To view a more detailed command history that displays the execution status of each command along with its start and end times, run the following command:

```bash
PS C:\> Get-History | Format-List -Property *
```

By default, the `Get-History` cmdlet only shows the 32 most recent history entries. If you want to view or search a larger number of history entries, use the `-Count` option to specify how many history entries PowerShell should show, like so:

```bash
PS C:\> Get-History -Count 1000

PS C:\> Get-History -Count 1000 | Select-String -Pattern "Example"

PS C:\> Get-History -Count 1000 | Format-List -Property *
```

### How to Clear Your PowerShell History

To clear the history of commands you've typed, run the following cmdlet:
```
PS C:\> Clear-History
```

##### note: you can also use `history` command to get that.

### `exit` Command

to close your terminal you can use this command.

```bash
PS C:\> exit
```

| Commands                   | Explanations                     | Usage                            |
| -------------------------- | -------------------------------- | -------------------------------- |
| `cls` <br>`clear`          | to clear your previous commands. | `cls`<br>`clear`                 |
| `Get-History`<br>`history` | gets the session history         | `Get-History -flag`<br>`history` |
| `exit`                     | to close your terminal           | `exit`                           |

## File and Folders management


### ``cd`` Command 

cd will change drive and directory, both. you can use this command to navigate into your directories.
for example :

```bash
PS C:\> cd Q:\MyDir
PS Q:\> MyDir
```

### ``ls`` Command
you can easily list your files and directories with this command

```bash
PS C:\> ls
file1.format
file2.format
.
.
.

```

note : you can also use `dir` command.
### `pwd` Command

The _pwd_ command in PowerShell is used to display the current working directory. It is an alias for the _Get-Location_ cmdlet, which returns an object representing the current directory

```bash
PS C:\> pwd
Path
----
C:\Users\YourUsername
```

### `tree` Command

The _tree_ command in PowerShell is a useful tool for displaying the directory structure of a specified path or drive. It graphically represents the folder hierarchy, making it easier to visualize the organization of files and directories.
#### Basic Usage

To display the directory structure of the current directory, simply use the _tree_ command without any parameters:

```bash
PS C:\> tree
```

#### Displaying Files

By default, the _tree_ command only shows the names of folders. To include the names of the files within each folder, use the `/f` parameter:

```bash
PS C:\> tree /f
```

For example, if your current directory is `c:\users\bobbi\data1`, running the `tree /f` command will display the folder structure along with the files inside each folder:

```bash
c:
├───athletes
│ new_data.txt
│ old_data.txt
├───coaches
 |	│ records.txt
└───managers
 |	├───admin
 |	└───roster
```


### `mv` Command
You can use this command to move or rename your files and directories.

rename items :
```shell
PS C:\myfolder\> mv myfile.format myNewNameFile.format
```

moving items :
```shell
PS C:\myfolder\> mv myfile.format C:\myNewPath\myNewNameFile.format
```

### ``cp`` Command
You can copy your files and directories by using this command.
for example :

```bash
PS C:\> cp c:\data\file1.doc D:\backup\file2.doc
```

also you can use copy command.

```bash
PS C:\> copy c:\data\file1.doc D:\backup\file2.doc
```

### `mkdir` Command

You can make directories with this command.
```shell
PS C:\> mkdir folderName
```

### ``rm`` Command

you can use rm command for deleting items.
for example you have a file named `myfile.txt` and you want to remove it (also it works with folders).
```shell
PS C:\> rm myfile.txt
```

now think you have a folder named with `myFolder` and there is some files and another folders for example we have a file named with `myfile.txt` inside that when you running this command you will have this output.

```shell
PS C:\> rm .\myFolder\

Confirm
The item at C:\myFolder\ has children and the Recurse parameter was not specified.
If you continue, all children will be removed with the item. Are you sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

and you should confirm your operation to delete your files.

also you can delete all of files and folders inside a folder (and also delete all of files with a specific format.)

for example:

```bash
PS C:\myfolder\> rm *.*
```

```shell
PS C:\myfolder\> rm *.txt*
```

it will delete all of your txt files inside your folder.

### `cat` Command

this command have many usages lets see.

##### Displaying content of a file
Think you have a txt file named file.txt and you wrote inside that `Hello World`.
```shell
PS C:\> cat file.txt
Hello World
```

##### Appending Contents
Now think you have 2 files named file1.txt and file2.txt inside of each one for example we have `Hello my friend.` and `How are you ?`.
if you run this command you will have this.

```shell
PS C:\> cat file2.txt >> file1.txt
```

now lets see content of file1.txt

```shell
PS C:\> cat file1.txt
Hello my friend
How are you ?
```

### `diff` Command

`diff` Command is used to compare two sets of objects, including files or text content, and identifies differences between them.

#### Usage : 

```shell
PS C:\> diff (Get-Content file1.txt) (Get-Content file2.txt)
```

### Example Output

If `file1.txt` contains:

```
apple
banana
carrot
```


And `file2.txt` contains:

```
apple
banana
date
```

The output of the comparison will be:
```
carrot => 
<= date
```

This shows `carrot` is only in `file1.txt`, and `date` is only in `file2.txt`.

| Commands | Explanations                                                                                                                                 | Usage                                                                                                   |
| -------- | -------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| `cd`     | Use this command to move your directory to another one.                                                                                      | `cd \path\to\myfolder`<br><br>`cd ..` (to back previous folder)<br><br>`cd\` (to back your root folder) |
| `dir`    | With this command you can list all of your items in your directory.                                                                          | `dir`                                                                                                   |
| `ls`     | like as dir command but usually uses in unix base systems like as linux and others.<br>note : in command prompt (CMD) this command no exist. | `ls`                                                                                                    |
| `cp`     | Use this command to copy files and folders to another directory.                                                                             | `cp /path/to/myfile /path/to/new`<br><br>`cp -r /path/to/myfolder /path/to/new`                         |
| `rm`     | Use this command to remove files and directories                                                                                             | `rm /path/to/myfile`<br><br>`rm -rf /path/to/directory`                                                 |
| `del`    | like as rm command but in Microsoft Windows command prompt (CMD) we can just use del commmand                                                | `del /path/to/myfile`                                                                                   |
| `pwd`    | to get your current address                                                                                                                  | `pwd`                                                                                                   |
| `tree`   | to display your directory structure                                                                                                          | `tree` `tree /f`                                                                                        |
| `mkdir`  | to create folders.                                                                                                                           | `mkdir foldername`                                                                                      |
| `mv`     | to move or rename files.                                                                                                                     | `mv file newNamefile`<br><br>`mv file /newpath/file`                                                    |
| `cat`    | to display content of a file or append content of two files.                                                                                 | `cat file.txt`<br><br>`cat file1st.txt >> file2nd.txt`                                                  |
| diff     | to get difference between two objects                                                                                                        | `diff <objc1> <objc2>`                                                                                  |

### Variables

##### `echo` Command

the echo command uses to print a string to powershell or put a string in a file for example :
```shell
PS C:\> echo "Hello World"
Hello World
```

putting in a file :
```shell
PS C:\> echo "Hello World" >> file.txt
```

```shell
PS C:\> echo "Hello World" > file.txt
```

the difference between `>` (one shift) and `>>` (double shift) operations is the one shift will overwrites your file and delete the previous data in your file but double shift will append the string at the end of your file.

## Internet

#### `ping` Command

to get latency of your Internet and check your connection.

```shell
PS C:\> ping google.com
```

if you want run ping for limited count you can run this for example : 

```shell
PS C:\> ping google.com -c 4
```

### `curl` Command

one of the usages of curl command is downloading files from links.
```shell
PS C:\> curl -o filename.format https://example.com/filename.format
```

here is `-o` flag which is means output name and location of file.
```shell
PS C:\> curl -o myfolder\filename.format https://example.com/filename.format
```
### `winget` Command

winget is a package manager for Windows (like as apt or pacman in linux systems) actually Microsoft Store based on winget you can use winget to update or install and uninstall your apps.

#### Installing a package :
```shell
PS C:\> winget install package_name
```

##### example :

```shell
PS C:\> winget install vscode
```


#### Updating installed packages

```shell
PS C:\> winget upgrade
```

#### Uninstalling a Packege

```shell
PS C:\> winget uninstall package_name
```

##### example :

```shell
PS C:\> winget uninstall vscode
```
