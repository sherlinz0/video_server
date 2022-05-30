# video server
基于 `node` 快速创建一个流媒体服务器

`ffmpeg` 推流步骤：
1. 查看媒体设备:

`ffmpeg -list_devices true -f dshow -i dummy`

2. 推流

``` powershell
ffmpeg -f dshow -i video=“Integrated Camera”:audio=“麦克风阵列 (Realtek(R) Audio)” -vcodec libx264 -acodec copy -preset:v ultrafast -tune:v zerolatency -f flv “rtmp://localhost:1935/live/home"
// 其中 Integrated Camera 是你的照相机设备名称, 麦克风阵列 (Realtek(R) Audio), rtmp://localhost:1935/live/home 是你的推流地址，将 localhost:1935 换成你自己的ip地址即可
```