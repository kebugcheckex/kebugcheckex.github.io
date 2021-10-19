---
layout: post
title: Simple Video Editing with FFmpeg
category: video
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

## File Operations

### Concatenating a series of files

```
ffmpeg -f concat -i files.txt output.mp4
```

where `files.txt` contains the list of files to concatenate. The format is

```
file '/path/to/file1'
file '/path/to/file2'
```

Reference: [Concatenating media files](https://trac.ffmpeg.org/wiki/Concatenate)
