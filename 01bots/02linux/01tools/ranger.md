# Ranger

## resources

1. [Digital Ocean Setup Page](https://www.digitalocean.com/community/tutorials/installing-and-using-ranger-a-terminal-file-manager-on-a-ubuntu-vps)
2. [Keybindings](http://dquinton.github.io/debian-install/files/ranger-keybinds_quinton.pdf)

## tweaks

1. Ranger supports git status display. But people report tha this does make it slow to start with sometimes so what you can do is the following settings in your conf to enable is when you need the info

   ```bash
   # Keep the vcs aware false
   set vcs_aware false
   
   # But set a hotkey to use it when required.
   map zg set vcs_aware true
   ```

2. You can add column to your ranger panes by changing the following property

    ```bash
    # Draw borders around columns?
    set draw_borders true
    ```

