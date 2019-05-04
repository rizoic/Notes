# TIPS

1. How do you prevent a directory from any edits in Linux?

   Use **chattr**. You can say `sudo chattr -R +i dirname` to prevent any edits to it even as sudo. The `+i` stands for making it immutable. The `-R` is an argument to do this recursively for all subdirs.  Regarding immutability from the chattr manual

   ```markdown
      A file with the 'i' attribute cannot be modified: it cannot be deleted or renamed, no link can be created to this file and no data can be written to the file.  Only the superuser or a process possess‐ing the CAP_LINUX_IMMUTABLE capability can set or clear this attribute.
   ```
   To remove the mutability just run `chattr -R -i dirname`. You can check the dirstatus with **`lsattr`**

