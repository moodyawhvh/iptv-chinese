> 🌐 本文档由 [iptv-org/iptv](https://github.com/iptv-org/iptv) 翻译,英文原版见原项目。

# 直播流描述方案

一条直播流要想通过审核,其描述必须遵循以下模板:

```m3u
#EXTINF:-1 tvg-id="STREAM_ID",STREAM_TITLE (QUALITY) [LABEL]
STREAM_URL
```

| 属性           | 说明                                                                                                                                                                            | 是否必填 | 有效值                                       |
| -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------- | -------------------------------------------- |
| `STREAM_ID`    | 流 ID,由频道 ID 和信号源(feed)ID 组成。所有受支持频道及其对应 ID 的完整列表可在 [iptv-org.github.io](https://iptv-org.github.io/) 查阅。                                        | 可选     | `<channel_id>` 或 `<channel_id>@<feed_id>`   |
| `STREAM_TITLE` | 流标题,由频道名称和信号源名称组成。可包含除 `,`、`[`、`]` 之外的任意字符。                                                                                                       | 必填     | -                                            |
| `QUALITY`      | 直播流最高画质。                                                                                                                                                                 | 可选     | `2160p`、`1080p`、`720p`、`480p`、`360p` 等   |
| `LABEL`        | 当广播因某些原因可能对部分用户不可用时标注。                                                                                                                                     | 可选     | `Geo-blocked` 或 `Not 24/7`                   |
| `STREAM_URL`   | 直播流 URL。支持以下协议:`HTTPS`、`HTTP`、`MMS`、`MMSH`、`RTSP`、`RTMP`、`SRT`、`RTP`、`UDP`。                                                                                   | 必填     | -                                            |

示例:

```m3u
#EXTINF:-1 tvg-id="ExampleTV.us@East",Example TV East (720p) [Geo-blocked]
https://example.com/playlist.m3u8
```

此外,如有需要,还可以通过 `#EXTVLCOPT` 指令指定自定义的 [HTTP User-Agent](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/User-Agent) 和 [HTTP Referrer](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Referer):

```m3u
#EXTINF:-1 tvg-id="ExampleTV.us",Example TV
#EXTVLCOPT:http-referrer=http://example.com/
#EXTVLCOPT:http-user-agent=Mozilla/5.0 (Windows NT 10.0; Win64; x64)
http://example.com/stream.m3u8
```
