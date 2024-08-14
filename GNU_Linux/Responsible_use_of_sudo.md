# Responsible Use of `sudo`

This reading will delve deeper into `sudo`, particularly focusing on the responsible use of elevated privileges and additional commands like `usermod` and `chown`.

## The Importance of Responsible `sudo` Usage

### Why Use `sudo` Instead of Root?

To manage authorization and authentication effectively, you need elevated privileges. Traditionally, this is done by logging in as the root user, also known as the "super user." However, using the root account directly is not recommended due to the following risks:

- **Security Risks**: If malicious actors compromise the root account, they gain complete control over the system.
- **Irreversible Mistakes**: Running commands as root can easily lead to mistakes that could cause irreparable damage.
- **Lack of Accountability**: The system cannot track which user executed a command when using the root account.

### The Role of `sudo`

The `sudo` command temporarily grants elevated permissions to specific users without requiring them to log in as the root user. This is safer as it allows users to perform necessary tasks with elevated privileges while maintaining security and accountability.

However, because `sudo` grants elevated permissions, it must be used carefully. Only users who genuinely need these permissions should have access to `sudo`, similar to how a master key in a hotel should only be given to trusted personnel. 

**Important:** Always be cautious when copying and executing commands that include `sudo` from online sources. Misuse of `sudo` can lead to unintended consequences.

## Authentication and Authorization with `sudo`

Authentication verifies a user’s identity, while authorization determines what resources they can access. Here are some key `sudo`-enabled commands for managing users and permissions:

### `useradd`

The `useradd` command adds a new user to the system. For example:

```bash
sudo useradd fgarcia
```

This adds a user with the username `fgarcia`.

**Options for `useradd`:**

- **`-g`**: Sets the user’s primary group.
  - Example: `sudo useradd -g security fgarcia`
- **`-G`**: Adds the user to supplemental groups.
  - Example: `sudo useradd -G finance,admin fgarcia`

### `usermod`

The `usermod` command modifies existing user accounts. For example:

- **Change primary group**: `sudo usermod -g executive fgarcia`
- **Add to supplemental groups**: `sudo usermod -a -G marketing fgarcia`

**Important**: When modifying supplemental groups, always use the `-a` option with `-G` to append new groups without removing existing ones.

**Other useful options:**

- **`-d`**: Changes the user’s home directory.
  - Example: `sudo usermod -d /home/garcia_f fgarcia`
- **`-l`**: Changes the user’s login name.
- **`-L`**: Locks the user account, preventing login.

### `userdel`

The `userdel` command deletes a user from the system:

```bash
sudo userdel fgarcia
```

This deletes the user `fgarcia`. 

**Options for `userdel`:**

- **`-r`**: Deletes the user and their home directory.
  - Example: `sudo userdel -r fgarcia`

**Tip**: Instead of deleting a user, consider deactivating their account with `usermod -L` to retain access to their files and permissions for later review.

### `chown`

The `chown` command changes the ownership of a file or directory. For example:

- **Change user ownership**: `sudo chown fgarcia access.txt`
- **Change group ownership**: `sudo chown :security access.txt`

**Note**: The colon `:` before the group name in the second example designates it as a group.

## Key Takeaways

- **Authentication** verifies a user's identity, while **authorization** determines their access rights.
- Use `sudo` to safely execute commands with elevated privileges, minimizing security risks.
- Commands like `useradd`, `usermod`, `userdel`, and `chown` are essential for managing users and file ownership in a secure and controlled manner.
