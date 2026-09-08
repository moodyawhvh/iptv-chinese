> 🌐 本文档由 [iptv-org/iptv](https://github.com/iptv-org/iptv) 翻译,英文原版见原项目。

# 直播流测试

要确认一条直播流链接能否正常观看,只需按下面几个简单步骤操作:

1. 用一个支持 [HLS](https://en.wikipedia.org/wiki/HTTP_Live_Streaming) 或 [DASH](https://en.wikipedia.org/wiki/Dynamic_Adaptive_Streaming_over_HTTP) 流的媒体播放器打开它。下文的示例中我们使用 [VLC media player](https://www.videolan.org/vlc/index.html)。
2. 观看广播至少一分钟,确认播放稳定、不会突然中断(有些测试流会在 15–30 秒后截断)。
3. 尝试重新打开该直播流,确认它不是在循环播放同一段内容,并且仍然可用。

如果直播流无法播放,试着打开播放器的错误日志,通常能在那里找到确切原因。在 VLC 中,它位于 `工具 -> 消息`(Tools -> Messages)。

如果直播流在你的媒体播放器里放不出来,但在网页浏览器中却一切正常,问题很可能出在缺少 [HTTP User-Agent](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/User-Agent) 和/或 [HTTP Referrer](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Referer) 请求头。

这时,在浏览器中打开该直播流,按 `F12`,切换到 **Network**(网络)标签页,然后过滤 `m3u` 或 `mpd` 请求:

<img width="338" height="256" alt="image" src="https://github.com/user-attachments/assets/2eec24df-21a4-4a77-8a96-4f967baf2548" />

接着切换到 **Headers**(标头)标签页,往下滚动,复制 `User-Agent` 和 `Referer` 的值:

<img width="660" height="425" alt="image" src="https://github.com/user-attachments/assets/6e0c4453-3e56-4ad3-86a7-c9430c33c188" />

然后打开任意文本编辑器,把链接和刚找到的参数按如下格式粘贴进去:

```m3u
#EXTM3U
#EXTINF:-1,Example TV
#EXTVLCOPT:http-referrer=https://example.com
#EXTVLCOPT:http-user-agent=Mozilla/5.0 (Windows NT 10.0; Win64; x64)
https://example.com/playlist.m3u8
```

把文件保存为 `.m3u` 扩展名,再用媒体播放器打开它。大多数情况下,它应该立刻就能播放。

要测试仓库中已有的链接,直接运行 [playlist:test](./scripts.md#playlisttest) 脚本即可。
