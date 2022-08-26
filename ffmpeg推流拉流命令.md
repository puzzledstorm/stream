# ffmpeg推流rtmp
```
ffmpeg -re -i test.flv -c copy -f flv rtmp://server/live/streamName
-re 减慢推流的帧率
-c copy 表示将流直接拷贝

本地视频推流
ffmpeg -re -i 桥本环奈.flv -f flv rtmp://127.0.0.1:1935/live/123

```
# ffmpeg拉流
```
ffmpeg -i rtmp://server/live/streamName -c copy dump.flv
```


# 超星学习通推流
```
参考： https://blog.wolf4096.top/9.wolf
```

# [rtmp](https://en.wikipedia.org/wiki/Real-Time_Messaging_Protocol)
```
Real-Time Messaging Protocol (RTMP) is communication technology that enables live video streaming over the internet. 
It’s based on Transmission Control Protocol (TCP) technology and was originally developed by Macromedia for their Flash Player, 
which later became Adobe Flash Player after the company was acquired by Adobe.
```
