# Navigate Linux and Read File Content

In this reading, you’ll review how to navigate the file system using **Linux commands** in **Bash**. You’ll further explore the organization of the **Linux Filesystem Hierarchy Standard (FHS)**, review several common **Linux commands** for navigation and reading file content, and learn a couple of new commands.

## Filesystem Hierarchy Standard (FHS)

Previously, you learned that the **Filesystem Hierarchy Standard (FHS)** is the component of Linux that organizes data. The **FHS** is important because it defines how directories, directory contents, and other storage is organized in the operating system.

This diagram illustrates the hierarchy of relationships under the **FHS**:

![illustrates the hierarchy of relationships under the **FHS**]([URL](https://github.com/Walid-El-Hioul/Courses/blob/main/GNU_Linux/Photos/Hierarchy_of_relationships_under_the_FHS.png))

**Root Directory**
The **root directory** is the highest-level directory in Linux, and it’s always represented with a forward slash (`/`). All subdirectories branch off the **root directory**. Subdirectories can continue branching out to as many levels as necessary.

**Standard FHS Directories**
Directly below the root directory, you’ll find standard **FHS directories**. Here are a few examples of what standard directories contain:

- `/home`: Each user in the system gets their own home directory.
- `/bin`: This directory stands for “binary” and contains binary files and other executables.
- `/etc`: This directory stores the system’s configuration files.
- `/tmp`: This directory stores many temporary files. The `/tmp` directory is commonly used by attackers because anyone in the system can modify data in these files.
- `/mnt`: This directory stands for “mount” and stores media, such as USB drives and hard drives.

**Pro Tip:** You can use the `man hier` command to learn more about the **FHS** and its standard directories.

**User-Specific Subdirectories**
Under **/home** are subdirectories for specific users. Each user has their own personal subdirectories, such as **projects**, **logs**, or **reports**.

**Note:** When the path leads to a subdirectory below the user’s home directory, the user’s home directory can be represented as the tilde (`~`). For example, `/home/analyst/logs` can also be represented as `~/logs`.

You can navigate to specific subdirectories using their **absolute** or **relative file paths**. The **absolute file path** is the full file path, which starts from the root. For example, `/home/analyst/projects` is an absolute file path. The **relative file path** is the file path that starts from a user's current directory.

**Note:** Relative file paths can use a dot (`.`) to represent the current directory, or two dots (`..`) to represent the parent of the current directory. An example of a relative file path could be `../projects`.

## Key Commands for Navigating the File System

The following **Linux commands** can be used to navigate the file system:

### `pwd`
The `pwd` command prints the working directory to the screen. It returns the directory that you’re currently in. For example, if you’re in your home directory and your username is `analyst`, entering `pwd` returns `/home/analyst`.

**Pro Tip:** To learn what your username is, use the `whoami` command. The `whoami` command returns the username of the current user.

### `ls`
The `ls` command displays the names of the files and directories in the current working directory. For example, `ls` might return directories such as **logs**, and a file called **updates.txt**.

**Note:** If you want to return the contents of a directory that’s not your current working directory, you can add an argument after `ls` with the absolute or relative file path to the desired directory.

### `cd`
The `cd` command navigates between directories. When you need to change directories, use this command.

To navigate to a subdirectory of the current directory, add an argument after `cd` with the subdirectory name. For example, `cd projects` changes the directory to `projects`.

You can also navigate to any specific directory by entering the absolute file path. For example, `cd /home/analyst/logs` changes your current directory to `/home/analyst/logs`.

**Pro Tip:** You can use the relative file path and enter `cd ..` to go up one level in the file structure.

## Common Commands for Reading File Content

The following **Linux commands** are useful for reading file content:

### `cat`
The `cat` command displays the content of a file. For example, `cat updates.txt` returns everything in the `updates.txt` file.

### `head`
The `head` command displays just the beginning of a file, by default 10 lines. For example, `head updates.txt` returns only the first 10 lines of the `updates.txt` file.

**Pro Tip:** To change the number of lines returned by `head`, use `-n`. For example, `head -n 5 updates.txt` displays the first five lines.

### `tail`
The `tail` command displays just the end of a file, by default 10 lines. For example, `tail updates.txt` returns only the last 10 lines of the `updates.txt` file.

**Pro Tip:** Use `tail` to read the most recent information in a log file.

### `less`
The `less` command returns the content of a file one page at a time. For example, `less updates.txt` displays the contents one page at a time.

Once you’ve accessed your content with the `less` command, you can use several keyboard controls to move through the file:
- **Space bar:** Move forward one page
- **b:** Move back one page
- **Down arrow:** Move forward one line
- **Up arrow:** Move back one line
- **q:** Quit and return to the previous terminal window

## Key Takeaways

It’s important for security analysts to be able to **navigate Linux** and the file system of the **FHS**. Some key commands for navigating the file system include **pwd**, **ls**, and **cd**. Reading file content is also an important skill in the security profession. This can be done with commands such as **cat**, **head**, **tail**, and **less**.
