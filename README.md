# Linux File System Hierarchy – Training Notes

## 1. Introduction to Linux File System Hierarchy

- Linux uses a hierarchical directory structure.
- The root directory `/` is the starting point of the Linux file system.
- All files, directories, devices, and mounted file systems are organized under `/`.
- Linux follows the Filesystem Hierarchy Standard (FHS), although implementations vary by distribution.

### Linux File System Architecture

### Important Linux Directories

| Directory | Purpose                                     |
| --------- | ------------------------------------------- |
| `/`       | Root of the file system                     |
| `/home`   | Regular users' home directories             |
| `/root`   | Root user's home directory                  |
| `/bin`    | Essential user commands                     |
| `/sbin`   | Essential system administration commands    |
| `/etc`    | System configuration files                  |
| `/var`    | Variable data, including logs               |
| `/tmp`    | Temporary files                             |
| `/usr`    | User applications, libraries, and utilities |
| `/opt`    | Optional third-party software               |
| `/boot`   | Bootloader and kernel-related files         |
| `/dev`    | Device files                                |
| `/proc`   | Virtual process and kernel information      |
| `/sys`    | Virtual kernel and device information       |
| `/mnt`    | Temporary mount points                      |
| `/media`  | Removable media mount points                |

Note: On modern Linux distributions, `/bin` and `/sbin` are often symbolic links into `/usr`.

## 2. Difference Between Home Directory and Working Directory

| Home Directory                              | Working Directory                  |
| ------------------------------------------- | ---------------------------------- |
| Default personal directory of a user        | Directory currently being accessed |
| Usually `/home/username`                    | Can be any accessible directory    |
| Represented by `~`                          | Represented by `.`                 |
| Check using `echo $HOME`                    | Check using `pwd`                  |
| Typically remains the same during a session | Changes when using `cd`            |

### Example

```
whoami
echo $HOME
pwd

cd /etc
pwd

cd ~
pwd
```

Points to Remember

- `~` → Home directory
- `.` → Current directory
- `..` → Parent directory
- `/` → Root directory
- `-` → Previous working directory when used with `cd`

## 3. Directory Navigation Commands

| Command    | Description                       |
| ---------- | --------------------------------- |
| `pwd`      | Display current working directory |
| `ls`       | List directory contents           |
| `ls -l`    | Long listing format               |
| `ls -a`    | Show hidden files                 |
| `ls -lh`   | Human-readable file sizes         |
| `cd /`     | Navigate to root                  |
| `cd /home` | Navigate to `/home`               |
| `cd ~`     | Navigate to home directory        |
| `cd ..`    | Move one level up                 |
| `cd ../..` | Move two levels up                |
| `cd -`     | Switch to previous directory      |
| `cd`       | Return to home directory          |
| `tree`     | Display directory tree            |
| `ls -R`    | List directories recursively      |

### Practical Commands

```
pwd
ls
ls -l
ls -la
ls -lh

cd /
pwd

cd /etc
ls

cd /var/log
ls

cd ~
pwd
```

## 4. Absolute Path and Relative Path

| Absolute Path                   | Relative Path                     |
| ------------------------------- | --------------------------------- |
| Starts with `/`                 | Usually does not start with `/`   |
| Begins from the root directory  | Begins from the current directory |
| Independent of current location | Depends on current location       |
| Example: `/home/atul/docs`      | Example: `docs`                   |

### Absolute Path Example

```
cd /home
cd /etc
cd /var/log
```

### Relative Path Example

```
cd /home
cd atul
cd Documents
cd ..
cd ../..
```

### Path Navigation Example

Current directory: `/home/atul`

```
# Absolute path
cd /var/log

# Return home
cd ~

# Relative path
cd Documents

# Parent directory
cd ..

# Previous directory
cd -
```

## 5. Hands-on Practice & Exploration

### Lab 1 – Explore Linux File System

```
pwd
ls /
ls /home
ls /etc
ls /var
ls /usr
ls /tmp
```

### Lab 2 – Create Directory Structure

```
cd ~
mkdir linux-lab
cd linux-lab

mkdir documents
mkdir projects
mkdir backups

ls -l
```

### Lab 3 – Navigate Directories

```
cd documents
pwd

cd ..
cd projects
pwd

cd ../backups
pwd

cd ~
```

### Lab 4 – Create Files and Explore

```
cd ~/linux-lab

touch file1.txt
touch file2.txt

ls -l
ls -la

mkdir -p projects/aws/ec2

cd projects/aws/ec2
pwd
```

### Lab 5 – Explore System Directories

```
ls /etc
ls /var/log
ls /proc
ls /dev

cat /etc/os-release
uname -r
```

### Lab 6 – Directory Tree

```
# Amazon Linux / RHEL
sudo dnf install tree -y

# Ubuntu
sudo apt install tree -y

# Display hierarchy
tree ~/linux-lab
```

### Expected Directory Structure

```
/home/atul/linux-lab/
├── backups/
├── documents/
├── file1.txt
├── file2.txt
└── projects/
    └── aws/
        └── ec2/
```

## 6. Practice Assignments

- Identify the Linux root directory.
- Display the current working directory.
- Navigate to `/etc` using an absolute path.
- Navigate to `/var/log`.
- Return to the home directory.
- Create a directory named `linux-practice`.
- Create three subdirectories: `aws`, `azure`, and `devops`.
- Navigate using relative paths.
- Create two empty files using `touch`.
- Display the complete directory tree.

## 7. Points to Remember

1. Linux has a single hierarchical directory tree starting at `/`.
2. `/root` and `/` are different directories.
3. `/home` stores regular users' home directories by convention.
4. `pwd` shows the current working directory.
5. `cd` changes the working directory.
6. Absolute paths begin with `/`.
7. Relative paths are resolved from the current working directory.
8. Linux file and directory names are case-sensitive.
9. `ls -la` displays hidden files and detailed information.
10. Avoid modifying system directories during basic exploration.

Training outcome: Students should be able to identify important Linux directories, navigate the file system, distinguish absolute and relative paths, and create and explore directory structures through the command line.
