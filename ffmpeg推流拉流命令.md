# ffmpeg推流rtmp
```
ffmpeg -re -i test.flv -c copy -f flv rtmp://server/live/streamName
-re 减慢推流的帧率
-c copy 表示将流直接拷贝

ffmpeg -re -stream_loop -1 -i video.mp4 -f flv -c copy -flvflags no_duration_filesize rtmp://192.168.183.43:1935/stream/2333
-stream_loop -1 无限循环推流

本地视频推流
ffmpeg -re -i 桥本环奈.flv -f flv rtmp://127.0.0.1:1935/live/123

ffmpeg同时推流一个视频和一张图片，交替进行循环推流
ffmpeg -stream_loop -1 -re -i video_8k.mp4 -loop 1 -i image_8k.jpg -filter_complex "[0:v]setpts=PTS-STARTPTS, scale=1280x720[v0]; [1:v]setpts=PTS-STARTPTS, scale=1280x720[v1]; [v0][v1]concat=n=2:v=1:a=0[out]" -map "[out]" -f flv rtmp://172.22.0.52/live/livestream/123

ffmpeg同时推流一个8K视频和一张8K图片，交替进行循环推流
ffmpeg -stream_loop -1 -re -i video_8k.mp4 -loop 1 -i image_8k.jpg -filter_complex "[0:v]setpts=PTS-STARTPTS, scale=7680x4320[v0]; [1:v]setpts=PTS-STARTPTS, scale=7680x4320[v1]; [v0][v1]concat=n=2:v=1:a=0[out]" -map "[out]" -f flv rtmp://172.22.0.52/live/livestream/123

ffmpeg -stream_loop -1 -re -i video_8k.mp4 -vf "scale=7680x4320" -c:v libx264 -preset ultrafast -maxrate 8000k -bufsize 8000k -f flv rtmp://172.22.0.52/live/livestream/123

ffmpeg -re -loop 1 -i image_8k.jpg -t 1 -f flv rtmp://172.22.0.52/live/livestream/123 && ffmpeg -re -stream_loop -1 -i video_8k.mp4 -f flv rtmp://172.22.0.52/live/livestream/123

这个才能做到ffmpeg同时推流一个8K视频和一张8K图片，交替进行循环推流
@echo off
:loop
ffmpeg -re -loop 1 -i image_8k.jpg -t 2 -f flv rtmp://172.22.0.52/live/livestream/123
ffmpeg -re -i video_8k.mp4 -f flv rtmp://172.22.0.52/live/livestream/123
goto loop

```
# ffmpeg拉流
```
ffmpeg -i rtmp://server/live/streamName -c copy dump.flv
```

# ffplay播放rtmp流
```
ffplay -i rtmp://127.0.0.1:1935/live/123
```

# ffmpeg win10本地nginx rtmp推流拉流搭建
参考： https://blog.csdn.net/u013554213/article/details/87342605
```
nginx.exe -c conf\nginx-win-rtmp.conf
ffmpeg -re -i 经典广告合集.flv -f flv rtmp://127.0.0.1:1935/live/stream
ffplay -fs rtmp://127.0.0.1:1935/live/stream
```

# 超星学习通推流
```
参考： https://blog.wolf4096.top/9.wolf
```

# ffmpeg win10本地nginx rtmp推流拉流搭建
参考： https://blog.csdn.net/u013554213/article/details/87342605
```
nginx.exe -c conf\nginx-win-rtmp.conf
ffmpeg -re -i 经典广告合集.flv -f flv rtmp://127.0.0.1:1935/live/stream
ffplay -fs rtmp://127.0.0.1:1935/live/stream
```

# [rtmp](https://en.wikipedia.org/wiki/Real-Time_Messaging_Protocol)
```
Real-Time Messaging Protocol (RTMP) is communication technology that enables live video streaming over the internet. 
It’s based on Transmission Control Protocol (TCP) technology and was originally developed by Macromedia for their Flash Player, 
which later became Adobe Flash Player after the company was acquired by Adobe.
```
ref: https://zhuanlan.zhihu.com/p/73984438
