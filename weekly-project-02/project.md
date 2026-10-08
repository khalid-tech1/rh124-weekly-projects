# Weekly Project 02 — NorthStar Access & Permissions Administration

**Style:** RH124 + real-world Linux administration  
**Coverage:** Cumulative practice through Chapter 7  
**Main focus:** Chapter 6 and Chapter 7  
**Primary topics:** users, groups, sudo, password aging, ownership, permissions, umask, setgid, sticky bit  
**Reinforcement:** paths, files, directories, links, redirection, and basic verification  
**Excluded:** Chapter 8 process management, Chapter 9 services, `man`, and `vim`

---

# Scenario

You are a junior Linux administrator at **NorthStar IT Services**.

The company is preparing a shared Linux environment for three teams:

- Linux Operations
- Network Operations
- Security Audit

Your job is to create the required users and groups, build secure shared directories, configure ownership and permissions, apply password-aging rules, create a limited sudo policy, and verify that access behaves as expected.

This project is intentionally centered on **user/group administration and permissions**. File-management tasks are included only where they support those goals.

---

# Part 1 — Prepare the Lab Workspace

## Task 1

Create a project directory in your home directory named:

```text
weekly-project-02
```

Enter it and confirm your location.

## Task 2

Create this structure:

```text
weekly-project-02/
├── reports/
├── backup/
├── notes/
└── verification/
```

Use one `mkdir` command where practical.

## Task 3

Create these files:

```text
reports/access-review.txt
reports/account-review.txt
notes/admin-notes.txt
```

## Task 4

Display the project tree.

---

# Part 2 — Create Department Groups

## Task 5

Create these local groups:

```text
platformops
networkteam
secaudit
collabops
```

## Task 6

Verify that all four groups exist.

## Task 7

Create one additional group named:

```text
reviewsudo
```

This group will be used later for a limited sudo policy.

---

# Part 3 — Create Local Users

## Task 8

Create these local users:

```text
wp2admin
wp2tech
wp2trainee
```

Each account must have:

- a home directory
- `/bin/bash` as the login shell

## Task 9

Verify all three users with a command that shows their passwd database entries.

## Task 10

Display each user's:

- UID
- primary GID
- supplementary groups

---

# Part 4 — Supplementary Group Membership

## Task 11

Add `wp2admin` to:

```text
platformops
collabops
```

as supplementary groups.

## Task 12

Add `wp2tech` to:

```text
networkteam
collabops
```

as supplementary groups.

## Task 13

Add `wp2trainee` to:

```text
secaudit
collabops
```

as supplementary groups.

## Task 14

Add `wp2admin` to:

```text
reviewsudo
```

without removing any existing supplementary memberships.

## Task 15

Verify the final group memberships of all three users.

---

# Part 5 — Primary vs Supplementary Groups

## Task 16

Identify the primary group of:

```text
wp2admin
```

## Task 17

Identify all supplementary groups of:

```text
wp2admin
```

## Task 18

Temporarily switch the active group of `wp2admin` to:

```text
platformops
```

using the appropriate command.

## Task 19

While the active group is `platformops`, create:

```text
~/group-test.txt
```

as `wp2admin`.

Then inspect the file's group ownership.

## Task 20

Exit the temporary group shell and verify `wp2admin`'s normal group information again.

---

# Part 6 — Password Aging

## Task 21

Configure `wp2trainee` so that:

- maximum password age = 90 days
- warning period = 7 days

## Task 22

Display the password-aging information for `wp2trainee`.

## Task 23

Configure `wp2tech` so that the account itself expires on:

```text
2026-12-31
```

## Task 24

Verify the account-expiration setting for `wp2tech`.

## Task 25

Record the password-aging information for both users in:

```text
reports/account-review.txt
```

Do not overwrite the first user's information when adding the second.

---

# Part 7 — Build Shared Department Directories

## Task 26

Create this structure under `/srv`:

```text
/srv/northstar-wp2/
├── linux/
├── network/
├── audit/
└── project/
```

Use `sudo`.

## Task 27

Set ownership as follows:

```text
/srv/northstar-wp2/linux    root:platformops
/srv/northstar-wp2/network  root:networkteam
/srv/northstar-wp2/audit    root:secaudit
/srv/northstar-wp2/project  root:collabops
```

## Task 28

Set all four directories so that:

- owner has full access
- group has full access
- others have no access

Use octal permissions.

## Task 29

Verify ownership and permissions for all four directories.

---

# Part 8 — Setgid Shared Directories

## Task 30

Enable `setgid` on all four shared directories while keeping:

```text
rwxrwx---
```

for owner, group, and others.

## Task 31

Verify that `setgid` is visible in the group execute position.

## Task 32

As `wp2admin`, create:

```text
/srv/northstar-wp2/linux/linux-note.txt
```

## Task 33

As `wp2tech`, create:

```text
/srv/northstar-wp2/network/network-note.txt
```

## Task 34

As `wp2trainee`, create:

```text
/srv/northstar-wp2/audit/audit-note.txt
```

## Task 35

Verify the group ownership of all three files.

Each file should inherit the group of its parent directory.

---

# Part 9 — Cross-Team Access Testing

## Task 36

As `wp2admin`, attempt to create a file inside:

```text
/srv/northstar-wp2/network/
```

Record whether access is allowed or denied.

## Task 37

As `wp2tech`, attempt to create a file inside:

```text
/srv/northstar-wp2/audit/
```

Record the result.

## Task 38

As `wp2trainee`, attempt to create a file inside:

```text
/srv/northstar-wp2/linux/
```

Record the result.

## Task 39

Append the three access-test results to:

```text
reports/access-review.txt
```

Use clear labels for each test.

---

# Part 10 — Shared Project Directory

## Task 40

Verify that all three users belong to:

```text
collabops
```

## Task 41

As `wp2admin`, create:

```text
/srv/northstar-wp2/project/admin-project.txt
```

## Task 42

As `wp2tech`, create:

```text
/srv/northstar-wp2/project/tech-project.txt
```

## Task 43

As `wp2trainee`, create:

```text
/srv/northstar-wp2/project/trainee-project.txt
```

## Task 44

Verify that all three files inherited:

```text
collabops
```

as their group.

---

# Part 11 — Umask Practice

## Task 45

Open a login shell as `wp2admin`.

Temporarily set:

```text
umask 027
```

## Task 46

Create:

```text
/srv/northstar-wp2/linux/umask027.txt
```

Verify its permissions.

## Task 47

Change the temporary umask to:

```text
007
```

Create:

```text
/srv/northstar-wp2/linux/umask007.txt
```

Verify its permissions.

## Task 48

Compare the permissions of:

```text
umask027.txt
umask007.txt
```

and record the result in:

```text
notes/admin-notes.txt
```

## Task 49

Exit the `wp2admin` shell.

Do not make either umask permanent.

---

# Part 12 — Sticky Bit

## Task 50

Enable the sticky bit on:

```text
/srv/northstar-wp2/project
```

Keep setgid enabled and keep owner/group access at `rwx`.

Others should still have no access.

## Task 51

Verify the final permission string for:

```text
/srv/northstar-wp2/project
```

## Task 52

As `wp2admin`, attempt to delete:

```text
/srv/northstar-wp2/project/tech-project.txt
```

Record the result.

## Task 53

As `wp2trainee`, attempt to delete:

```text
/srv/northstar-wp2/project/admin-project.txt
```

Record the result.

## Task 54

Verify that both files still exist.

---

# Part 13 — Ownership Changes

## Task 55

Create:

```text
/srv/northstar-wp2/audit/security-review.txt
```

as root.

## Task 56

Change the file owner to:

```text
wp2trainee
```

and keep the group as:

```text
secaudit
```

## Task 57

Change only the group ownership of:

```text
/srv/northstar-wp2/network/network-note.txt
```

to:

```text
collabops
```

Do not change the file owner.

## Task 58

Verify the ownership of both files.

---

# Part 14 — Symbolic and Octal chmod

## Task 59

Set:

```text
/srv/northstar-wp2/audit/security-review.txt
```

to:

```text
rw-r-----
```

using octal mode.

## Task 60

Verify the permission string.

## Task 61

Using symbolic mode, add group write permission to the same file.

## Task 62

Using symbolic mode, remove owner write permission from the same file.

## Task 63

Verify the final permissions.

---

# Part 15 — Limited Sudo Policy

Use `/etc/sudoers.d/`. Do not edit `/etc/sudoers` directly.

## Task 64

Create a sudo policy file named:

```text
/etc/sudoers.d/northstar-wp2-review
```

The policy should allow members of:

```text
reviewsudo
```

to run this command with sudo:

```text
/usr/bin/tail
```

## Task 65

Set the sudo policy file permissions to:

```text
0440
```

## Task 66

Validate the sudo configuration.

Do not continue until the syntax is valid.

## Task 67

As `wp2admin`, display the sudo permissions available to that user.

## Task 68

As `wp2admin`, use the allowed sudo command to display the last five lines of:

```text
/etc/group
```

## Task 69

As `wp2admin`, attempt a different sudo command that was not granted by this policy.

Record the result.

---

# Part 16 — Final Verification

## Task 70

Display the final group entries for:

```text
platformops
networkteam
secaudit
collabops
reviewsudo
```

## Task 71

Display the final identity information for:

```text
wp2admin
wp2tech
wp2trainee
```

## Task 72

Display ownership and permissions for:

```text
/srv/northstar-wp2/linux
/srv/northstar-wp2/network
/srv/northstar-wp2/audit
/srv/northstar-wp2/project
```

## Task 73

Display the contents and permissions of:

```text
/srv/northstar-wp2/linux/
```

## Task 74

Display the contents and permissions of:

```text
/srv/northstar-wp2/network/
```

## Task 75

Display the contents and permissions of:

```text
/srv/northstar-wp2/audit/
```

## Task 76

Display the contents and permissions of:

```text
/srv/northstar-wp2/project/
```

## Task 77

Display:

```text
reports/access-review.txt
reports/account-review.txt
notes/admin-notes.txt
```

## Task 78

Verify the sudo policy file:

```text
/etc/sudoers.d/northstar-wp2-review
```

including its ownership and permissions.

## Task 79

Display the final project tree under:

```text
~/weekly-project-02
```

## Task 80

Create:

```text
verification/project-complete.txt
```

containing:

```text
Weekly Project 02 completed and verified
```

Display the file.

---

# Main Skills Practiced

```text
groupadd
useradd
usermod -aG
id
getent
newgrp
chage
sudo
sudo -l
sudoers.d
chmod 0440
visudo -c
chown
chgrp
symbolic permissions
octal permissions
umask
setgid
sticky bit
shared directories
access testing
```

Chapter 8 process-management topics are intentionally excluded from this project.
