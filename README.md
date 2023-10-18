POC of package creation, installation and uninstallation

# POC layout

* `source/webserver` - the webserver directory as it is in the sandbox. This is the source for the package.
* `target/webserver` - simulated target webserver directory on the SIEM VM
* `clean` - a clean copy of the target to reset the POC and to compare the result

# Input to the package

`list.txt` contains the list of files and directories to be included into the package, relative to the webserver directory

# Creating the package

```
$ bash pack list.txt source/webserver package.tgz
```

This creates `package.tgz` in the current directory. You need to copy `package.tgz`, `install` and `uninstall` to the target VM.

# Installing the package

```
$ bash install package.tgz target/webserver backup
```

This makes a backup copy of modified files and unpacks `package.tgz` into the webserver folder.

# Uninstalling the package

```
$ bash uninstall package.tgz target/webserver backup
```

This deletes the files and folders added by the package and restores the modified files from the backup.

