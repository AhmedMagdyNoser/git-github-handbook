# Windows PowerShell Common Commands

## Changing Directory

- `cd /` - Returns to root (e.g., C:\\)

- `cd ..` - Goes back one folder

- `cd folderName` - Enters the specified folder

- `cd "path"` - Navigates to the specified path

## Making Directory

- `md newFolderName` - Creates a new folder

- `md Folder1, Folder2` - Creates multiple folders

- `md "path\newFolderName"` - Creates a folder at a specific path

## Creating New Files

- `new-item fileName.extension` - Creates a new file

- `new-item file1.ext, file2.ext` - Creates multiple files

- `new-item "path\newfile.ext"` - Creates a file at a specific path

## Other Commands

- `ls` or `dir` - Lists files and folders in current directory

- `move (file/folder) (folder/"path")` - Moves or renames files/folders

- `copy (file/folder) (folder/"path")` - Copies files/folders

- `rm (file/folder)` - Deletes files/folders

- `echo text > file` - Creates a file with text

- `echo text >> file` - Appends text to a file

- `type file` - Displays file contents

- `type file1 > file2` - Copies content to a new file

- `get-help command` - Shows command details

## Loops

```powershell
for ( $i = 0; $i -lt 10; $i++ ) { md $i }
```
