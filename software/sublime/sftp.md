# SFTP

Sync files with ease.

## Installation

Requires [Package Control](https://github.com/MaxOSmith/eg/sublime/README.md), for installation. 

1. (Ctrl/Cmd)+Shift+p
2. In the command palette window select *Package Control: Install Package*, you may just start typing any part of it and hit enter when it's highlighted.
3. In the next window select *SFTP*.

## Usage

### Basic

1. View > Side-bar > Show Side Bar
2. Drag the folder you want to sync-up into the side-bar, and you'll now have a convenient way to navigate your files. 
3. Right-click on your folder, SFTP/FTP > Map to Remote ...
4. This will give you a new file `sftp-config.json`, which is the configuration file. This is in JSON format, which should be pretty intuitive. 
5. The main settings we're concerned with are `host`, `user`, and `remote_path`. **Do not put your password in this file.**
  - `host`: this is the server you want to sync your files with, for CAEN this is: `login.engin.umich.edu`.
  - `user`: this is the username you use to login to your server, for CAEN this would be your uniqname. 
  - `remote_path`: the path to the folder on the server that you want to sync-to.
Here's an example of the final product (just the lines of interest):
  ```javascript
      "host": "login.engin.umich.edu",
      "user": "mxsmith",
      //"password": "password",
      //"port": "22",
      
      "remote_path": "/home/mxsmith/16W/EECS_482/Projects/p3/",
  ```
6. Now you can right-click on a file and upload it to the remote path (SFTP/FTP > Upload File)
7. You may find this annoying to have to upload on every save manually. Setting `upload_on_save` to `true` will automagically upload the file whenever it is saved. Check out the other options and see if they interest you. Also check out the options in the right-click menu for SFTP/FTP and familiarize yourself with your options.

### Tips

- You should add `sftp-config.json` to your `.gitignore` file for those using Git as version control.
- If you have a fun `.bashrc`, it might cause SFTP to hang on connection. To circumvent this, which is an issue of only loading your profile for certain shell types, modify your `.bashrc` to something of this nature:

  ```bash
  if [ "$SSH_TTY" ]
  then
    source ~/profile/.bashrc
  fi
  ```
- j

## References
- https://wbond.net/sublime_packages/sftp
- http://rdxiang.github.io/programming/sublime-sftp/
