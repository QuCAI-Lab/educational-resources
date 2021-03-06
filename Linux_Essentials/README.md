<br />
<div align="center"> 
  <a href="https://www.linux.org/"><img align="center" src="https://www.linux.org/images/logo.png"></a>
  <h1> Linux Essentials (call it Hacks) </h1>
</div>

<br />

<!--- ####################################################################################################################################################################### -->

Check out [explainshell.com](https://explainshell.com/) for an interactive alternative to Linux man pages that enables you to quick parse queried commands.

# Ubuntu Prelims 

Beware: the angle brackets punctuation mark denoted by "`<>`" (voiced chevrons) is only used as a placeholder, i.e, it's not a special character.

- Ubuntu version:

```bash
$ lsb_release -a
```

- Current user:

```bash
$ who
```

- Command manual:

```bash
$ man <command>
```

- To open Gnome file manager in the current directory:

```bash
$ nautilus .
```

- Root privileges:

```bash
$ sudo su
```

<!--- ####################################################################################################################################################################### -->

## Packages

- Adding an external repository:

```bash
$ sudo add-apt-repository
```

- Package Update:

```bash
$ sudo apt-get update
```

- Package Installation:

```bash
$ sudo apt-get install <package-name>
```

- Packakge Uninstallation
```bash
$ sudo apt-get purge --auto-remove <file>
```
and (to remove the aptitude cache)
```bash
$ sudo apt-get clean
```
Note: the flag `--purge` remove the configuration files, and the flag `--auto-remove` removes associated packages.

- List installed packages:
```bash
$ dpkg --list
```
Note: press 'q' to exit mode.
or (to locate a file in dpkg list)
```bash
$ dpkg --list | grep file
```
or 
```bash
apt list --installed
```
or (to list specifics)
```bash
apt list -a <package_name>
```
or
```bash
apt list -a sudo
```

- Locate (binary, source, and manual) files of a command:

```bash
whereis <file>
```

- Display file pathname:

```bash
which -a <file>
```

## [TAR-based files](https://explainshell.com/explain?cmd=tar+-xvzf#):

- Extracting:

(tar -xvzf to unpack a .gz file)
```bash
$ tar -xvzf <filename>.tar.gz
```
(tar -xvjf to unpack a .bz2 file)
```bash
$ tar -xvjf <filename>.tar.bz2
```
or (tar -xf to unpack a .xz file)
```bash
$ tar -xf <filename>.tar.xz
```
or (gunzip to unpack .gzip file)
```bash
$ gunzip <filename>.gz
```

- Installing:
```bash
$ ./configure
$ make
$ sudo make install
```

## .sh files:

Grant execute permission:
```bash
$ chmod +x <file>.sh
```

Run/install the file:
```bash
$ ./<file>.sh
```

## Debian packages:

- Install:
```bash
$ sudo dpkg -i package.deb
```
Or 
```bash
$ sudo dpkg --install package.deb
```
- Remove:
```bash
$ sudo dpkg -r package.deb
```
Or 
```bash
$ sudo dpkg --remove package.deb
```

<!--- ####################################################################################################################################################################### -->

## Directory

- Path of the current working directory:

```bash
$ pwd
```

- Creating a folder/directory:

```bash
$ mkdir <dir-name>
```
Tip: the `mkdir` command works in both Unix-like (Linux, macOS) and Windows command-line interpreters.


- Deleting a directory:

```bash
$ rmdir <dir-name>
```

- Deleting a non-empty directory:

```bash
$ rm -r <dir-name>
```

- Switch to a specific folder/directory:

```bash
$ cd <dir-name>
```
or (if the directory name has spaces)
```bash
cd '<dir name with space>'
```

- Switching to Home directory:

```bash
$ cd ~
```

- Switch to root directory:

```bash
$ cd /
```

- Switch to one level up dir.:

```bash
$ cd ..
```

- Switch to the previous dir.:

```bash
$ cd -
```

<!--- ####################################################################################################################################################################### -->

## Files

- To read a file (.txt, .md, .yml):

```bash
$ less <filename>
```
or (to open the file with gedit)

```bash
$ gedit <filename>
```

- To read a .pdf file:

```bash
$ evince <filename.pdf>
```

- Listing files in the current directory:

```bash
$ ls
```
or (to list hidden files)
```bash
$ ll
```
or (to list content information)
```bash
$ ls -l
```
or (to list the allocated size of each file, in blocks)
```bash
$ ls -s
```

- Creating a `.txt` file:

```bash
$ cat > <filename>.txt 
```
or (to create and add a text string to the file)
```bash
$ echo "This is a string" > <filename>.txt
```

- Updating a `.txt` file:

```bash
$ echo "new text string" >> <filename>.txt
```

- Cloning a file to the current directory:

```bash
$ cp -iv ~/<path-dir-name>/<filename> .
```

Note1: the `-i` flag stands for `interactive mode` and enables the user to choose to overwrite the file.

Note2: the `-v` flag stands for `verbose`, to enable progress display.

Note3: flags can be concatenated, such as in `-iv`.

- Cloning a file to a different directory:

```bash
$ cp -iv ~/<path-dir-name> ~/<path-new-dir>/
```
or (for a file in the current directory)
```bash
$ cp -i filename ~/<path-new-dir>/
```

- Cloning all files from a specific dir. to a new dir.:

```bash
$ cp -a ~/<path-dir-name> ~/<path-new-dir>/
```

- Moving an entire directory:

```bash
$ mv -Ri ~/<path-dir-name> ~/<path-new-dir>/
```
Note: the `-R` flag stands for `recursive` mode.

- Renaming a file:

```bash
$ mv <filename.extension> <new-filename.extension>
```

- Deleting a file:

```bash
$ rm <filename>
```
or (to delete all files from the current directory)
```bash
$ rm *
```
or (to delete all files with `.png` extension in interactive mode)
```bah
$ rm -i *.png
```

<!--- ####################################################################################################################################################################### -->

## System

- Current system info:

```bash
$ uname -a
```

- System's memory usage:

```bash
$ free -h
```
or
```bash
$ free -m
```
```
'free' = wasted memory (not being used).
'available' = memory for allocation.
'buff/cache' = used memory for cache (Data has been read) and buffer (data is being written).
'free' + 'buff/cache' = 'available'.
```   

- CPU info (clock, cores, L2 and L3 cache memory...):

```bash
$ lscpu
```
Note: total threads = CPU core * threads per core.

- PCI (Peripheral Component Interconnect) buses (Wireless adapter, GPU...):

```bash
$ lspci
```
or (for an in-depth description)
```bash
$ lshw 
```
or (for short)
```bash
$ lshw - short
```

- On-board and off-board graphics card:

```bash
$ sudo lshw -C display
```

<!--- ####################################################################################################################################################################### -->

## Processes

- Top Processes:

```bash
$ top
```

- Running softwares:

```bash
$ ps -A 
```
or (for a specific software)
```bash
$ ps aux | grep <software_name>
```

- Display software PID:

```bash
$ pgrep <software_name>
```

- To kill a process:

```bash
$ sudo kill -9 <software_PID>
```


<!--- ####################################################################################################################################################################### -->

## Partition

- To list partition table:

```bash
$ sudo fdisk -l
```

- To list mount points (mounted drives/filesystem):

```bash
$ df -h
```

- To mount a partition:

```bash
$ sudo mount /dev/sdbX
```

<!--- ####################################################################################################################################################################### -->

## Flags on Google Colab 

- Graphics Card:

```jupyter
!nvidia-smi
```

# Contributors 

Created and maintained by [@camponogaraviera][1].

[1]: https://github.com/camponogaraviera
