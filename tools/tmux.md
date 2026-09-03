I use generic keybinds 

Copying from cli:
```
# enter the copy mode:
ctrl + b, [
# start marking the text:
ctrl + space and arrows
# copy:
ctrl + w 
# paste:
ctrl + b, ]
```

useful when working remotely.
ssh where you have to ssh 
over there:
```
tmux new -s work
```
when you're done then detach it
```
tmux ctrl-b d
```
once you come back
```
tmux ls
tmux attach -t <window-name-from-ls>
```

```
tmux kill-session -t <window-name-from-ls>
```
