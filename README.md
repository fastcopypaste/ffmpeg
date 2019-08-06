# ffmpeg
Useful commands with ffmpeg to save a lot of time

Official repository: https://github.com/FFmpeg/FFmpeg

Official documetation: https://ffmpeg.org/ffmpeg.html

Web mode: https://git.ffmpeg.org/ffmpeg

### Install ffmpeg

Please go here for detail document for all supported OS:
https://github.com/adaptlearning/adapt_authoring/wiki/Installing-FFmpeg

With Ubuntu:
```
sudo apt update
sudo apt install ffmpeg
ffmpeg -version
```

You can use `lsb_release -a` to check your Linux release name, and for example if you use Ubuntu 16.04 (Xenial), you can see the release here:
https://launchpad.net/ubuntu/+source/ffmpeg


### Common commands:

1. Render a video with custom bit rate:

```
ffmpeg -i source.mp4 -b {your bit rate} -strict -2 destination.mp4
```
{your bit rate} ~ 250000 is good enough

You can see detail here: https://unix.stackexchange.com/questions/28803/how-can-i-reduce-a-videos-size-with-ffmpeg

2. Join multi videos to one:

```
ffmpeg -f concat -safe 0 -i mylist.txt -c copy output.mp4
```

Content of `file list` like this:
```
file '1.mp4'
file '2.mp4'
file '3.mp4'
```
3. Record screen in Linux:

```
ffmpeg -f x11grab  -s 1280x1024 -i :1 -r 25 -vcodec libx264  output.mkv
```
You can change `1280x1024` with this:
```
xrandr -q --current | grep '*' | awk '{print$1}'
```

4. Cut video if from start to end:

```
ffmpeg -i in.mp4 -ss 00:00:00 -t 00:01:28 -async 1 -strict -2 cut.mp4
```
