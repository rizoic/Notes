# XCLIP

[xclip](https://github.com/astrand/xclip) is a handly command line utility to copy things from the command line to your clipboard. You can easily pipe things to it and then get those things in your clipboard



## XCLIP over SSH

1. Change `X11Forwarding` to *yes* in `/etc/ssh/sshd_config`. Understand that this has security risks. From the man for `ssh`:

   >  X11 forwarding should be enabled with caution.  Users with the ability to bypass file permissions on the remote host (for the user's X authorization database) can access the local X11 display through the forwarded connection.  An attacker may then be able to perform activities such as keystroke monitoring.

So it is safe primarily for internal machines not exposed to the internet.

2. Now install xclip on the ssh machine
3. Now you can simple pipe anything to xclip and have it copied into the clipboard.
4. One thing to note here though is the two types of clipboards `primary` and `clipboard`. Primary is one where you can paste by middle click of mouse while clipboard is the one where you can paste by `Ctrl + V`
5. You can add the following aliases to your bash

```bash
# For the default clipboard
alias c='xclip -selection clipboard'
alias v='xclip -selection clipboard -o'

# For the primary clipboard
alias cp='xclip -selection primary'
alias vp='xclip -selection primary -o'
```

6. Now use the aliases as follows
```bash
# Copy from pipe or a file
echo "Test"|c
c testfile.txt

# Paste 
v

# If you are doing it out of the terminal you can use normal Ctrl+V
```
