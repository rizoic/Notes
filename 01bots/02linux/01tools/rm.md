# RM

1. Have a safer version of rm [safe-rm](https://github.com/kaelzhang/shell-safe-rm). This will move all the deleted files to a temporary directory from where they can be restored manually if needed. Also another thing it has on top is a whitelist which it will not delete. You can keep critical directories in this whitelist. 

   Post installing safe-rm from its repository you can add an alias to your bashrc like so

   ```bash
   alias rm='/bin/safe-rm
   ```

   Ok but we know it is just moving but what if we we want to delete a huge set of files. We cannot afford to move it to trash. In such cases there is a nifty hack that you can use which is preprending `\` to an alias i.e.

   ```bash
   # In this case bash will run the original rm and thus no moving to the trash dir
   \rm test.txt
   ```
   
   
   
   

