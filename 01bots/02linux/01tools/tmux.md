# Tmux

1. Tumx can be very handy for launching a command in the background so that it doesnt take control of the terminal or throws any of its output to the current terminal. The very cool thing about this is that once the command/app finishes tmux will automatically close the session.

```bash
tmux new-session -d -s "pycharm" ~/pycharm-community/bin/pycharm.sh
```

Very clean handling of a background process. Can be used very well for IGV/Jupyter/GSEA/Pycharm.

