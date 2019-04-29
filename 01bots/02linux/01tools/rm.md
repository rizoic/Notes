# RM

1. Have a safer version of rm [safe-rm](https://github.com/kaelzhang/shell-safe-rm). This will move all the deleted files to a temporary directory from where they can be restored manually if needed. Also another thing it has on top is a whitelist which it will not delete. You can keep critical directories in this whitelist. 

   Post installing safe-rm from its repository you can add an alias to your bashrc like so

   ```bash
   alias rm='/bin/safe-rm
   ```

   Also what you can do is 

   