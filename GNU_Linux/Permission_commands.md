# Managing Permissions

In this reading, you’ll review these concepts and focus on an example of how these commands work together when applying the principle of least privilege.

## Reading Permissions

In Linux, permissions are represented with a 10-character string. Permissions include:

- **Read**: 
  - For files: The ability to read the file contents.
  - For directories: The ability to read all contents in the directory, including files and subdirectories.
  
- **Write**: 
  - For files: The ability to modify the file contents.
  - For directories: The ability to create new files in the directory.
  
- **Execute**: 
  - For files: The ability to execute the file if it’s a program.
  - For directories: The ability to enter the directory and access its files.

These permissions are assigned to three types of owners:

- **User**: The owner of the file.
- **Group**: A larger group that the owner is part of.
- **Other**: All other users on the system.

### Understanding the Permission String

Each character in the 10-character string conveys different information about these permissions. Here's how the string is structured:

| Character Position | Example        | Meaning                                               |
|--------------------|----------------|-------------------------------------------------------|
| 1st                | `drwxrwxrwx`   | File type: `d` for directory, `-` for regular file    |
| 2nd                | `drwxrwxrwx`   | Read permissions for the user (`r` for read, `-` if not) |
| 3rd                | `drwxrwxrwx`   | Write permissions for the user (`w` for write, `-` if not) |
| 4th                | `drwxrwxrwx`   | Execute permissions for the user (`x` for execute, `-` if not) |
| 5th                | `drwxrwxrwx`   | Read permissions for the group (`r` for read, `-` if not) |
| 6th                | `drwxrwxrwx`   | Write permissions for the group (`w` for write, `-` if not) |
| 7th                | `drwxrwxrwx`   | Execute permissions for the group (`x` for execute, `-` if not) |
| 8th                | `drwxrwxrwx`   | Read permissions for others (`r` for read, `-` if not) |
| 9th                | `drwxrwxrwx`   | Write permissions for others (`w` for write, `-` if not) |
| 10th               | `drwxrwxrwx`   | Execute permissions for others (`x` for execute, `-` if not) |

## Exploring Existing Permissions

You can use the **`ls`** command to investigate who has permissions on files and directories. Here are some important **`ls`** options for security analysts:

- **`ls -a`**: Displays hidden files (hidden files start with a period `.`).
- **`ls -l`**: Displays permissions for files and directories, along with other details like owner name, group, file size, and time of last modification.
- **`ls -la`**: Displays permissions for all files and directories, including hidden ones (a combination of `-a` and `-l`).

## Changing Permissions

The principle of least privilege dictates granting only the minimal access required to complete a task. The **`chmod`** command helps manage this authorization by changing permissions on files and directories.

### Using `chmod`

The **`chmod`** command requires two arguments: 

1. **How** to change the permissions.
2. **What** file or directory to change permissions for.

Example: The following command would add all permissions (read, write, execute) to `login_sessions.txt`:

```bash
chmod u+rwx,g+rwx,o+rwx login_sessions.txt
```

To remove all permissions, you could use:

```bash
chmod u-rwx,g-rwx,o-rwx login_sessions.txt
```

Another way to assign these permissions is by using the equals sign (`=`). The `=` operator sets the permissions exactly as specified. For instance, the following command sets read permissions for `login_sessions.txt` for user, group, and other:

```bash
chmod u=r,g=r,o=r login_sessions.txt
```

This command overwrites existing permissions. If the user previously had write permissions, they would be removed after setting only read permissions.

### `chmod` Argument Characters

Here's a summary of how each character is used within the first argument of **`chmod`**:

| Character | Description                                               |
|-----------|-----------------------------------------------------------|
| `u`       | Changes user permissions                                  |
| `g`       | Changes group permissions                                 |
| `o`       | Changes other permissions                                 |
| `+`       | Adds permissions                                          |
| `-`       | Removes permissions                                       |
| `=`       | Assigns permissions (overwrites existing permissions)     |

**Note**: When changing permissions for more than one owner type, separate the changes with commas, without adding spaces.

## The Principle of Least Privilege in Action

As a security analyst, you may need to manage permissions based on the principle of least privilege. 

Example: There’s a file called `bonuses.txt` within a compensation directory. The owner, `hrrep1`, is a member of the HR department. The file contains confidential information, so only `hrrep1` should have access.

Running `ls -l` shows the permissions as `-rw-rw----`. The group owner has read and write permissions, which violates the principle of least privilege. To correct this, you would use:

```bash
chmod g-rw bonuses.txt
```

Now, only `hrrep1` has access to the file.

## Key Takeaways

Managing directory and file permissions is a critical part of a security analyst's work. Using **`ls`** with the `-l` and `-la` options allows you to investigate permissions, while **`chmod`** helps you align permissions with the principle of least privilege.
