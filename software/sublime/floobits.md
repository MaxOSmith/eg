# Floobits

Pair-programming the way it was meant to be.

## Installation

Requires [Package Control](https://github.com/MaxOSmith/eg/sublime/README.md), for installation. 

1. `(Ctrl/Cmd)+Shift+p`
2. In the command palette window select *Package Control: Install Package*, you may just start typing any part of it and hit enter when it's highlighted.
3. In the next window select *Floobits*.

## Usage

### Basic

Most of the functionality is through the command palette, which may be opened through `(Ctrl/Cmd)+Shift+p`. 

1. In the folder that you wish to make a workspace, think of this as a shared Google Drive folder, open the command palette and run the command `Floobits - Join Workspace`. 
2. This should prompt you for the workspace URL, which you may get by making a new workspace on Floobits.com and grabbing the URL. This will look something like `https://floobits.com/USERNAME/WORKSPACE`.
3. This will create two files `.floo` and `.flooignore`. The `.floo` file contains the configurations, like the workspace URL. And `.flooignore` is the files to ignore and not share, similar to Git's `.gitignore`. 

### Tips

- Add `sftp-config.json` to your `.flooignore`

1. 

## References
- https://floobits.com
- http://awan1.github.io/subl-floo-tutorial.html