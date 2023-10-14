---
title: Simple Video Editing with FFmpeg
layout: post
category: video
tags:
- ffmpeg
---

Professional video editing is usually done in Adobe Premiere or Final Cut Pro. However, for simple video editing tasks, such as cutting one segment out of a long video, or cropping the frame to a smaller size, etc., it is not necessary to use these bulky software, let alone they are quite expensive. Fortunately, `ffmpeg` is a free but powerful tool to solve these video editing tasks.

This article serves as a cookbook for frequently used video editing tasks using `ffmpeg`. It will be updated as new recipes emerges.

<!--more-->

## Video Size Modification

### Cropping frame

```
ffmpeg -i input.mp4 -filter:v "crop=width:height:left:top" output.mp4
```

The above command crops the input video from the `(left, top)` point using a rectangle with `width` and `height`.

### Resize Video

```
ffmpeg \
    -i input.mp4 \
    -vf scale=1280:720 \
    -fps_mode passthrough \
    -c:v libx264 \
    -b:v 1M \
    -c:a copy \
    output.mp4
```

With an NVIDIA GPU, you can significantely expedite the process
```
ffmpeg \
    -hwaccel cuvid \
    -hwaccel_output_format cuda \
    -c:v h264_cuvid \
    -resize 1280x720 \
    -i input.mp4 \
    -fps_mode passthrough \
    -c:v h264_nvenc \
    -c:a copy \
    -b:v 1M \
    output.mp4
```

Note that the code above requires the input to be encoded using H.264.

## File Operations

### Concatenating a series of files

```
ffmpeg -f concat -i files.txt output.mp4
```

where `files.txt` contains the list of files to concatenate[^1]. The format is

```
file '/path/to/file1'
file '/path/to/file2'
```

## Time Related Operations

### Cut Video By Time

```
ffmpeg \
    -i input.mp4 \
    -t 00:05:00 \
    -c copy part1.mp4 \
    -ss 00:05:00 \
    -c copy part2.mp4
```
Option `-t` specifies the time length of the output video and option `-ss` specifies the start timestamp. Combining these two options can be used to split or cut video by time.

## References

[^1]: [Concatenating media files](https://trac.ffmpeg.org/wiki/Concatenate)
