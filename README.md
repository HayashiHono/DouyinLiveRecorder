![video_spider](https://socialify.git.ci/ihmily/DouyinLiveRecorder/image?font=Inter&forks=1&language=1&owner=1&pattern=Circuit%20Board&stargazers=1&theme=Light)

## 💡简介
[![Python Version](https://img.shields.io/badge/python-3.11.6-blue.svg)](https://www.python.org/downloads/release/python-3116/)
![GitHub issues](https://img.shields.io/github/issues/ihmily/DouyinLiveRecorder.svg)
![Downloads](https://img.shields.io/github/downloads/ihmily/DouyinLiveRecorder/total)

一款可循环值守的直播录制工具，基于FFmpeg实现多平台直播源录制，支持自定义配置录制以及直播状态推送。

</div>

## 😺已支持平台

- [x] 抖音
- [x] Tiktok
- [x] 快手
- [x] 虎牙
- [x] 斗鱼
- [x] YY
- [x] B站
- [x] 小红书
- [x] bigo 
- [x] blued
- [ ] 更多平台正在更新中

</div>

## 🎈项目结构

```
.
└── DouyinLiveRecorder/
    ├── /api -> (get live stream api )
    ├── /config -> (config record)
    ├── /log -> (save runing log file)
    ├── /backup_config -> (backup file)
    ├── /libs -> (dll file)
    ├── main.py -> (main file)
    ├── spider.py-> (get live url)
    ├── utils.py -> (contains utility functions)
    ├── web_rid.py -> (get web_rid)
    ├── msg_push.py -> (send live status update message)
    ├── cookies.py -> (get douyin cookies)
    ├── x-bogus.js -> (get douyin xbogus token)
    ├── ffmpeg.exe -> (record video)
    ├── index.html -> (play m3u8 and flv video)
    ├── requirements.txt -> (library dependencies)
```

</div>

## 🌱使用说明

- 运行主文件main.py启动程序
- 在 `config` 文件夹内的配置文件中对录制进行配置，并在 `URL_config.ini` 中添加录制直播间地址。
- 抖音录制需要使用到PC网页端直播间页面的Cookie，请先在config.ini配置文件中添加后再进行抖音录制（有默认的cookie，但最好还是自己添加自己的）
- 录制Tiktok时需要科学上网，请先在配置文件中设置开启代理并添加proxy_addr链接 如：`http://127.0.0.1:7890`
- 可以在URL_config.ini中的链接开头加上#，此时将不会录制该条链接对应的直播
- 测试时有可能会出现在IDE如Pycharm中运行代码进行直播录制，录制出来的视频却无法正常播放的现象，如果遇到这个问题 在命令控制台DOS界面运行代码，录制出来的视频即可正常播放。
- 当同时在录制多个直播时，最好线程数设置大一些，否则可能出现其中一个直播录制出错。当然设置的过大也没用，要同时考虑自身电脑的配置，如CPU内核数、网络带宽等限制。
- 如果想直接使用打包好的录制软件，进入[Releases](https://github.com/ihmily/DouyinLiveRecorder/releases) 下载最新发布的 zip压缩包即可，有些电脑可能会报毒，直接忽略即可。
- 如果要长时间挂着软件循环监测直播，最好循环时间设置长一点，避免因请求频繁导致被官方封禁IP 。
- 最后，欢迎大家提交fork和PR

&emsp;

直播间链接示例：

```
抖音：
https://live.douyin.com/745964462470
https://v.douyin.com/iQFeBnt/

Tiktok：
https://www.tiktok.com/@pearlgaga88/live

快手：
https://live.kuaishou.com/u/yall1102

虎牙：
https://www.huya.com/52333

斗鱼：
https://www.douyu.com/3637778?dyshid=
https://www.douyu.com/topic/wzDBLS6?rid=4921614&dyshid=

YY:
https://www.yy.com/22490906/22490906

B站：
https://live.bilibili.com/320

小红书：
https://www.xiaohongshu.com/hina/livestream/568980065082002402?appuid=5f3f478a00000000010005b3&apptime=

bigo直播：
https://www.bigo.tv/cn/716418802

buled直播：
https://app.blued.cn/live?id=Mp6G2R
```

Tiktok目前只支持PC网页端地址（我没下载app），其他平台 app端直播间分享地址和网页端长地址都能正常进行录制（抖音尽量用长链接，避免因短链接转换失效导致不能正常录制）。

</div>

解析接口：

该解析接口 ~~仅供演示~~(演示接口暂时停止，后续再开放)，并且只包含抖音、快手、虎牙直播的解析，其他平台如有需要请自行添加，源码在这里 [DouyinLiveRecorder/api](https://github.com/ihmily/DouyinLiveRecorder/tree/main/api)

```HTTP
GET https://hmily.vip/api/jx/live/?url=
```

请求示例：

```HTTP
GET https://hmily.vip/api/jx/live/?url=https://live.douyin.com/573716250978
```

若需要将抖音直播间短链接转换为长链接，使用以下接口：

```HTTP
GET https://hmily.vip/api/jx/live/convert.php?url=https://v.douyin.com/iQLgKSj/
```

在线播放m3u8和flv视频网站：[M3U8 在线视频播放器 ](https://jx.hmily.vip/play/)



&emsp;

## ❤️贡献者

&ensp;&ensp; [![Hmily](https://github.com/ihmily.png?size=50)](https://github.com/ihmily)

</div>

## ⏳提交日志

- 20231207
  - 新增blued直播录制，修复YY直播录制，新增直播结束消息推送

- 20231206
  - 新增bigo直播录制

- 20231203
  - 新增小红书直播录制（全网首发），目前小红书官方没有切换清晰度功能，因此直播录制也只有默认画质
  - 小红书录制暂时无法循环监测，每次主播开启直播，都要重新获取一次链接
  - 获取链接的方式为 将直播间转发到微信，在微信中打开后，复制页面的链接。
- 20231030
  - 本次更新只是进行修复，没时间新增功能。
  - 欢迎各位大佬提pr 帮忙更新维护
- 20230930
  - 新增抖音从接口获取直播流，增强稳定性

  - 修改快手获取直播流的方式，改用从官方接口获取

  - 祝大家中秋节快乐！
- 20230919
  - 修复了快手版本更新后录制出错的问题，增加了其自动获取cookie(~~稳定性未知~~)
  - 修复了Tiktok显示正在直播但不进行录制的问题
- 20230907
  - 修复了因抖音官方更新了版本导致的录制出错以及短链接转换出错

  - 修复B站无法录制原画视频的bug

  - 修改了配置文件字段，新增各平台自定义设置Cookie
- 20230903
  - 修复了Tiktok录制时报644无法录制的问题
  - 新增直播状态推送到钉钉和微信的功能，如有需要请看 [设置推送教程](https://d04vqdiqwr3.feishu.cn/docx/XFPwdDDvfobbzlxhmMYcvouynDh?from=from_copylink)
  - 最近比较忙，其他问题有时间再更新
- 20230816
  - 修复斗鱼直播（官方更新了字段）和快手直播录制出错的问题
- 20230814
  - 新增B站直播录制
  - 写了一个在线播放M3U8和FLV视频的网页源码，打开即可食用
- 20230812
  - 新增YY直播录制
- 20230808
  - 修复主播重新开播无法再次录制的问题
- 20230807
  - 新增了斗鱼直播录制

  - 修复显示录制完成之后会重新开始录制的问题
- 20230805
  - 新增了虎牙直播录制，其暂时只能用flv视频流进行录制

  - Web API 新增了快手和虎牙这两个平台的直播流解析（Tiktok要代理）
- 20230804
  - 新增了快手直播录制，优化了部分代码
  - 上传了一个自动化获取抖音直播间页面Cookie的代码，可以用于录制
- 20230803
  - 通宵更新 
  - 新增了国际版抖音Tiktok的直播录制，去除冗余 简化了部分代码
- 20230724	
  - 新增了一个通过抖音直播间地址获取直播视频流链接的API接口，使用php写的 上传即可用


&emsp;

## 有问题可以提issue ，后续我会在这里不断更新其他直播平台的录制  欢迎Star

#### 
