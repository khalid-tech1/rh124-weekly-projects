# Weekly Project 02 — Linux Users, Groups & Permissions

## Scenario

This project simulates a junior Linux administrator preparing a shared Linux environment for several internal teams.

The main goal was to practice user and group administration together with secure shared-directory access, ownership, permissions, password aging, and limited sudo access.

## Main Focus

This project focused primarily on RH124 Chapter 6 and Chapter 7 topics:

- Local users and groups
- Primary and supplementary groups
- `newgrp`
- Password aging with `chage`
- Sudo permissions
- `/etc/sudoers.d/`
- Ownership with `chown` and `chgrp`
- Symbolic and octal permissions
- `umask`
- Setgid directories
- Sticky bit protection

## Practical Work

The lab included:

- Creating separate Linux, Network, Security, and collaboration groups
- Creating and assigning users to appropriate groups
- Testing cross-team access restrictions
- Building shared directories under `/srv`
- Using setgid for inherited group ownership
- Comparing file permissions created with different umask values
- Protecting shared files with the sticky bit
- Configuring a restricted sudo policy
- Validating sudo configuration before use

## Verification

The completed environment was verified using:

- `id`
- `getent`
- `chage -l`
- `ls -l`
- `ls -ld`
- `sudo -l`
- `visudo -c`

The verification also included real access tests between different users instead of relying only on permission listings.

## Status

**Completed and verified.**
