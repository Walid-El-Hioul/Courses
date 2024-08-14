Get Started:

1. **Create a Table:**
   ```sql
   CREATE TABLE users (
       id INTEGER PRIMARY KEY,
       name TEXT NOT NULL,
       email TEXT NOT NULL
   );
   ```

2. **Insert Data into the Table:**
   ```sql
   INSERT INTO users (name, email) VALUES ('Alice', 'alice@example.com');
   INSERT INTO users (name, email) VALUES ('Bob', 'bob@example.com');
   ```

3. **Query the Table:**
   ```sql
   SELECT * FROM users;
   ```

4. **List All Tables:**
   ```sql
   .tables
   ```

5. **Exit the SQLite Shell:**
   ```sql
   .exit
   ```

### Where is the Database File Located?

Your `myDB.db` database file is saved in the directory from which you ran the `sqlite3 myDB.db` command, which in this case is:

```
C:\Users\walid\Desktop\SQLite
```

You can navigate to this folder on your computer, and you should see the `myDB.db` file there. This file contains all the data and schema definitions you've created in your SQLite session.
