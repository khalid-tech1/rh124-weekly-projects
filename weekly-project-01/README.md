# Weekly Project 01 — Linux Administration

## Scenario

This project simulates a junior Linux administrator working in a small IT environment.

The goal was to combine previously completed RH124 topics into one practical project instead of practicing commands individually.

## Main Focus

The main focus of this project was:

- Building and managing a Linux project directory tree
- Working with absolute and relative paths
- Managing files and directories
- Using filename patterns and brace expansion

## Additional RH124 Topics Practiced

The project also included:

- Standard output and error redirection
- Pipelines
- `find`, `grep`, `sort`, `uniq`, `wc`, and `tee`
- Hard links and symbolic links
- Local users and groups
- Supplementary groups
- Password aging with `chage`
- Sudo administration
- File ownership
- Symbolic and octal permissions
- `umask`
- Setgid directories
- Sticky bit protection

## Verification Highlights

The final verification confirmed:

- Hard links shared the same inode
- Symbolic links worked correctly
- Users had the required supplementary groups
- Password aging was configured correctly
- Setgid caused files to inherit the directory group
- `umask 007` produced the expected file permissions
- Sticky bit prevented one user from deleting another user's file
- Project reports and verification files were created successfully

## Corrections Made

During the project, several small mistakes were identified and corrected, including:

- Directory naming errors
- Incorrect file placement
- A broken relative symbolic link
- Temporary files that had not initially been removed
- Minor redirection/output formatting issues

These corrections were part of the troubleshooting and learning process.

## Status

**Completed and verified.**
