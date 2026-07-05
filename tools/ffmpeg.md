## ffmpeg - program to make video much smaller in size 

```
# install
sudo apt update && sudo apt install ffmpeg -y
```


```
# choose one of those two:

ffmpeg -i input.mp4 -vcodec libx264 -crf 28 output.mp4

ffmpeg -i input.mp4 -vf scale=-1:720 -c:v libx264 -crf 28 output.mp4
```

