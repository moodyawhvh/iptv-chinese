> 🌐 本文档由 [iptv-org/iptv](https://github.com/iptv-org/iptv) 翻译,英文原版见原项目。

# 地域封锁

有时服务提供商会限制直播流在特定国家或地区播放。

为了避免把这类链接和失效链接混为一谈,我们会给它们打上 `Geo-blocked` 标签:

```m3u
#EXTINF:-1 tvg-id="ExampleTV.us@SD",Example TV (720p) [Geo-blocked]
https://example.com/playlist.m3u8
```

确认直播流在你的国家之外能否正常观看,最简单的办法是使用 [check-host.net](https://check-host.net/check-http) 这类在线检测服务,或者挂个 [VPN](https://en.wikipedia.org/wiki/Virtual_private_network)。
