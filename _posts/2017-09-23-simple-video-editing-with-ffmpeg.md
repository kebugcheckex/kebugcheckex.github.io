---
layout: post
title: Simple Video Editing with FFmpeg
tags: [video coding, ffmpeg]
---

I used to edit videos using Adobe Premiere back when I was working for the TV station of my university. Recently I need to do some simple video editing such as cutting one segment out of a long video, or cropping the frame to a smaller size, etc. It seems not very efficient to purchasing and download those gigantic Adobe software. Fortunately, we have the free, open source video coding software `ffmpeg` to help.

This article serves as a cookbook for frequently used video editing tasks. I will keep updating this article as I discover new requirements and solutions.

# Video Size Modification

## Cropping frame

`ffmpeg` has a set of powerful video filtering functions. Cropping the frame is easy:
```
ffmpeg -i input.mp4 -filter:v "crop=width:height:left:top" output.mp4
```
The above command crops the input video from the `(left, top)` point using a rectangle with `width` and `height`.
