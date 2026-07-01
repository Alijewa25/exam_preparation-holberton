## 🐧 Linux Shell — Basic Commands
 
**1. What does `pwd` do?**
Prints the current working directory (full path of where you are).
 
**2. Difference between `ls` and `ls -la`?**
`ls` lists files/folders in the current directory. `ls -la` shows **all** files (including hidden ones starting with `.`) in a **long/detailed** format (permissions, owner, size, date).
 
**3. What does `cd ..` do, and `cd ~` do?**
`cd ..` moves one directory up (to the parent folder). `cd ~` moves to the home directory.
 
**4. Difference between `touch file.txt` and creating a file with a text editor?**
`touch` creates an empty file instantly (or updates its timestamp if it exists) without opening any editor. A text editor opens an interface to write content into the file.
 
**5. What does `less` do, difference from `cat`?**
`less` opens a file for **scrollable, page-by-page viewing** (good for large files). `cat` prints the **entire file content at once** to the terminal.
 
**6. Difference between `cp` and `mv`?**
`cp` copies a file/folder (original stays). `mv` moves (or renames) a file/folder (original is removed from old location).
 
**7. What happens with `rm -r` on a folder? Why is `rm` dangerous?**
`rm -r` recursively deletes the folder and everything inside it. It's dangerous because there's **no trash/recycle bin** — deleted files are gone permanently.
 
**8. Difference between `mkdir` and `mkdir -p`?**
`mkdir` creates one directory (fails if parent folders don't exist). `mkdir -p` creates the directory **and any missing parent directories** along the path.
 
**9. Difference between `rmdir` and `rm -r`?**
`rmdir` only deletes an **empty** directory. `rm -r` deletes a directory **and all its contents**, even if it's not empty.
 
**10. Absolute path vs relative path?**
An **absolute path** starts from the root (`/`) and gives the full location, e.g. `/home/user/docs/file.txt`. A **relative path** is given from the current directory, e.g. `docs/file.txt` or `../file.txt`.