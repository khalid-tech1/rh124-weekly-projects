# Weekly Project 01 — NorthStar IT Linux Administration Lab

## Scenario

You have joined **NorthStar IT Services** as a junior Linux administrator.

Your first assignment is to prepare a small Linux workspace for the company’s Linux, Network, and Security teams. The environment does not need to be large, but it should be organized well enough that another administrator could understand it, use it, and verify your work.

This project is meant to feel closer to a real admin task than a command-by-command exercise. You are expected to choose the right command, verify your work, and correct mistakes when you find them.

The project covers RH124 topics completed through Chapter 7.

**Do not use `man` or `vim` for this project.**

---

# Part 1 — Get Oriented

## Task 1

Before changing anything, check where you are and who you are logged in as.

Display:

- your username
- your current working directory
- your home directory

## Task 2

Move to your home directory.

Create a new working directory named:

```text
northstar-it
```

Enter the directory.

## Task 3

Create a shell variable named:

```text
project_name
```

Store the absolute path of your `northstar-it` directory in it.

Display the variable to confirm that it contains the correct path.

---

# Part 2 — Build the Company Workspace

## Task 4

NorthStar wants separate areas for Linux, Network, Security, users, reports, backups, archives, and temporary files.

Create the following structure using **one `mkdir` command** where practical:

```text
northstar-it/
├── departments/
│   ├── linux/
│   │   ├── configs/
│   │   ├── scripts/
│   │   ├── notes/
│   │   └── logs/
│   ├── network/
│   │   ├── configs/
│   │   ├── reports/
│   │   └── diagrams/
│   └── security/
│       ├── logs/
│       ├── reports/
│       └── policies/
├── users/
│   ├── admin01/
│   ├── admin02/
│   └── trainee01/
├── reports/
├── backup/
├── archive/
└── temp/
```

Use brace expansion where it helps.

## Task 5

Inspect the full directory structure you just created.

Use `tree` if it is available. Otherwise, use a recursive `ls` command.

---

# Part 3 — Add Working Files

## Task 6

The Linux team has three server configuration files.

Create:

```text
server01.conf
server02.conf
server03.conf
```

inside:

```text
departments/linux/configs/
```

Create all three with one command.

## Task 7

The Linux team also keeps three shell scripts.

Create:

```text
backup.sh
monitor.sh
cleanup.sh
```

inside:

```text
departments/linux/scripts/
```

## Task 8

Create four Linux study notes:

```text
lesson1.txt
lesson2.txt
lesson3.txt
lesson4.txt
```

inside:

```text
departments/linux/notes/
```

Use brace expansion.

## Task 9

The Network team manages two routers and two switches.

Create:

```text
router01.conf
router02.conf
switch01.conf
switch02.conf
```

inside:

```text
departments/network/configs/
```

## Task 10

Create three Network team reports:

```text
report1.txt
report2.txt
report3.txt
```

inside:

```text
departments/network/reports/
```

## Task 11

The Security team needs log files for authentication and system activity.

Create:

```text
auth01.log
auth02.log
auth03.log
system01.log
system02.log
```

inside:

```text
departments/security/logs/
```

## Task 12

Create three Security audit reports:

```text
audit1.txt
audit2.txt
audit3.txt
```

inside:

```text
departments/security/reports/
```

---

# Part 4 — Hidden Project Files

## Task 13

Create these hidden files in the root of `northstar-it`:

```text
.project.conf
.inventory
```

## Task 14

Display the contents of `northstar-it` so that you can see:

- hidden files
- permissions and ownership
- human-readable file sizes

---

# Part 5 — Work with Paths

## Task 15

From the root of `northstar-it`, use a **relative path** to move into:

```text
departments/linux/notes
```

Confirm your location.

## Task 16

Without returning to your home directory, move from:

```text
departments/linux/notes
```

to:

```text
departments/security/logs
```

Use a relative path.

## Task 17

Use the `project_name` variable to return directly to the root of `northstar-it`.

Confirm your location.

---

# Part 6 — Back Up and Reorganize Files

## Task 18

Copy:

```text
departments/linux/configs/server01.conf
```

into:

```text
backup/
```

Keep the same filename.

## Task 19

Copy all Linux lesson `.txt` files into:

```text
backup/
```

Use one command.

## Task 20

Make a recursive backup of the entire:

```text
departments/network/
```

directory.

Place the copy inside:

```text
backup/
```

The final result should include:

```text
backup/network/
```

## Task 21

Move:

```text
departments/security/reports/audit3.txt
```

into:

```text
archive/
```

## Task 22

Rename the archived file from:

```text
audit3.txt
```

to:

```text
security-audit-old.txt
```

Do not use `cp`.

## Task 23

Move:

```text
departments/linux/notes/lesson4.txt
```

into `archive/` and rename it in the same command to:

```text
old-linux-lesson.txt
```

## Task 24

Create temporary files inside `temp/`:

```text
test1.tmp
test2.tmp
test3.tmp
old-data.txt
```

## Task 25

Delete only:

```text
old-data.txt
```

from the `temp` directory.

## Task 26

Use a filename pattern to delete all `.tmp` files from `temp/`.

Keep the `temp` directory itself.

---

# Part 7 — Links

## Task 27

The Linux team wants a second filename for `server01.conf` that points to the same inode.

Create a **hard link** named:

```text
server01-backup.conf
```

in the same directory as `server01.conf`.

## Task 28

Verify the hard link.

Your check should make it possible to compare:

- inode numbers
- link count

for both filenames.

## Task 29

The admin team wants quick access to the Linux configuration directory.

Inside:

```text
users/admin01/
```

create a symbolic link named:

```text
linux-configs
```

that points to:

```text
departments/linux/configs/
```

Make sure the link actually works.

## Task 30

Verify the symbolic link with a long listing, then access the target through the link to confirm it is not broken.

---

# Part 8 — Filename Patterns

## Task 31

Display every `.conf` file in:

```text
departments/linux/configs/
```

using `*`.

## Task 32

Display every `.log` file in:

```text
departments/security/logs/
```

using `*`.

## Task 33

Use `?` to display:

```text
report1.txt
report2.txt
report3.txt
```

from:

```text
departments/network/reports/
```

## Task 34

Use a character range to display only:

```text
lesson1.txt
lesson2.txt
lesson3.txt
```

from:

```text
departments/linux/notes/
```

## Task 35

Create these trainee files with one command:

```text
lab1.txt
lab2.txt
lab3.txt
lab4.txt
lab5.txt
lab6.txt
```

inside:

```text
users/trainee01/
```

Then use a filename range to display only:

```text
lab2.txt
lab3.txt
lab4.txt
lab5.txt
```

## Task 36

Use one command and a filename pattern to copy all Security `.log` files into:

```text
backup/
```

---

# Part 9 — Build a Simple System Report

## Task 37

Create:

```text
reports/system-summary.txt
```

using output redirection.

The first line should be:

```text
NorthStar IT System Summary
```

## Task 38

Append the following lines without overwriting the first line:

```text
Linux Team: Active
Network Team: Active
Security Team: Active
```

## Task 39

Append your current username and current working directory to the same report.

Use command substitution so the values are generated by commands.

Use labels similar to:

```text
User:
Working Directory:
```

## Task 40

Run an `ls` command against a path that does not exist.

Redirect only the error message to:

```text
reports/error.log
```

## Task 41

Generate a **different** `ls` error and append it to the same `error.log`.

Do not overwrite the first error.

---

# Part 10 — Pipelines and Text Processing

## Task 42

Count all `.txt` files anywhere under `northstar-it`.

Your command must use:

- `find`
- `-type f`
- `-name`
- a pipeline
- `wc -l`

## Task 43

Search:

```text
reports/system-summary.txt
```

and display only the lines containing:

```text
Active
```

## Task 44

Display the same report again, but this time exclude every line containing:

```text
Active
```

## Task 45

Create:

```text
reports/server-list.txt
```

with the following content:

```text
server03
server01
server02
server01
server03
server01
```

Then use a pipeline to display a sorted list with duplicate entries removed.

## Task 46

Run the sorted-and-unique pipeline again.

This time, use `tee` so the final result is:

- shown on the terminal
- saved to:

```text
reports/unique-servers.txt
```

---

# Part 11 — Create Local Groups and Users

> The following tasks make system-wide changes and require `sudo`.

## Task 47

Create these local groups:

```text
linuxops
netops
auditops
projectteam
```

Verify that all four groups exist.

## Task 48

Create these local users:

```text
nsadmin1
nstech1
nstrainee1
```

Each user should have:

- a home directory
- `/bin/bash` as the login shell

## Task 49

Add the users to supplementary groups as follows:

```text
nsadmin1    -> linuxops, projectteam
nstech1     -> netops, projectteam
nstrainee1  -> auditops, projectteam
```

Do not remove any existing supplementary group memberships by mistake.

## Task 50

Verify all three accounts.

Your output should clearly show:

- UID
- primary GID
- supplementary groups

## Task 51

Configure password aging for:

```text
nstrainee1
```

Use:

- maximum password age: `90` days
- warning period: `7` days

Verify the final account-aging settings.

---

# Part 12 — Sudo Administration

## Task 52

Use `sudo` to display the last 10 lines of:

```text
/etc/group
```

Do not modify the file.

## Task 53

Use `sudo` to copy:

```text
/etc/motd
```

to:

```text
/etc/motdOLD
```

Verify that the copied file exists.

## Task 54

Remove:

```text
/etc/motdOLD
```

using `sudo`.

Verify that it has been removed.

---

# Part 13 — Shared Directory Permissions

## Task 55

Create:

```text
/srv/northstar
```

and inside it create:

```text
linuxshare
teamdrop
```

Use `sudo`.

## Task 56

Set the ownership of:

```text
/srv/northstar/linuxshare
```

to:

```text
root:linuxops
```

## Task 57

Set the permissions on `linuxshare` so that:

- owner has full access
- group has full access
- others have no access

Use octal permissions.

## Task 58

Verify the current permissions and ownership.

Then apply the same permission set again using symbolic mode instead of octal mode.

The effective permissions should remain unchanged.

---

# Part 14 — Setgid in a Shared Team Directory

## Task 59

Enable `setgid` on:

```text
/srv/northstar/linuxshare
```

Keep the directory permissions equivalent to:

```text
rwxrwx---
```

for owner, group, and others.

Use octal mode.

## Task 60

As `nsadmin1`, create:

```text
/srv/northstar/linuxshare/admin-note.txt
```

Then verify the file's ownership and group.

Check whether the file inherited the directory's group.

---

# Part 15 — Umask

## Task 61

Open a shell as:

```text
nsadmin1
```

Temporarily set:

```text
umask 007
```

Create:

```text
/srv/northstar/linuxshare/umask-test.txt
```

Verify the resulting file permissions.

Do not make this umask permanent.

---

# Part 16 — Sticky Bit and Shared Access

## Task 62

Set the owner and group of:

```text
/srv/northstar/teamdrop
```

to:

```text
root:projectteam
```

Configure the directory so that:

- owner has `rwx`
- group has `rwx`
- others have no permissions
- setgid is enabled
- sticky bit is enabled

Use one octal mode.

## Task 63

As `nsadmin1`, create:

```text
/srv/northstar/teamdrop/admin-file.txt
```

As `nstech1`, create:

```text
/srv/northstar/teamdrop/tech-file.txt
```

Verify the owner and group of both files.

## Task 64

As `nstrainee1`, try to delete:

```text
/srv/northstar/teamdrop/admin-file.txt
```

Record the result.

Do not use root to bypass the test.

---

# Part 17 — Archive Completed Network Reports

## Task 65

Create:

```text
archive/completed-reports
```

inside your `northstar-it` project.

## Task 66

Use a filename pattern to move every `.txt` file from:

```text
departments/network/reports/
```

into:

```text
archive/completed-reports/
```

## Task 67

Verify both sides of the move:

- the original Network reports directory
- the completed reports archive

---

# Part 18 — Final Verification

## Task 68

Return to the root of:

```text
~/northstar-it
```

Display the final directory tree.

## Task 69

Display the project root with hidden files visible.

Confirm that both of these still exist:

```text
.project.conf
.inventory
```

## Task 70

Verify the following project items without changing them:

```text
backup/network/
archive/security-audit-old.txt
archive/old-linux-lesson.txt
archive/completed-reports/
users/admin01/linux-configs
reports/system-summary.txt
reports/error.log
reports/unique-servers.txt
```

## Task 71

Perform a final system-level verification.

Confirm:

```text
linuxops
netops
auditops
projectteam
```

and:

```text
nsadmin1
nstech1
nstrainee1
```

Also verify:

```text
/srv/northstar/linuxshare
/srv/northstar/teamdrop
```

Your final checks should make it possible to confirm:

- user and group existence
- supplementary group memberships
- ownership
- directory permissions
- setgid
- sticky bit

---

# Project Scope

This project combines previously completed RH124 topics through Chapter 7, with extra emphasis on practical filesystem work.

Topics practiced include:

```text
Filesystem navigation
Absolute and relative paths
Shell variables
Directory and file management
Brace expansion
Filename patterns
Hidden files
Hard links
Symbolic links
stdout and stderr redirection
Pipelines
find
grep
grep -v
sort
uniq
wc
tee
Users and groups
Supplementary groups
Password aging
sudo
Ownership
Symbolic and octal permissions
umask
setgid
sticky bit
```

**Excluded from this project:** `man`, `vim`, and Chapter 8 process-management topics.
