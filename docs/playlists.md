> 🌐 本文档由 [iptv-org/iptv](https://github.com/iptv-org/iptv) 翻译,英文原版见原项目。

# 播放列表

本仓库使用两类播放列表:内部播放列表和公开播放列表。

## 内部播放列表

这类播放列表位于 [streams/](../streams) 文件夹,包含仓库当前所有可用的链接。

这些播放列表中的链接按国家以及直播流来源服务分组。这样排列只是为了方便链接的审核管理。

最简单的形式下,一个内部播放列表长这样:

```
#EXTM3U
#EXTINF:-1 tvg-id="ExampleTV.us@SD",Example TV (720p)
https://example.com/playlist.m3u8
```

如果播放列表中的某个频道在我们的 [EPG](https://github.com/iptv-org/epg/blob/master/GUIDES.md) 仓库里有对应的节目指南,文件头还会包含指向它的链接:

```
#EXTM3U x-tvg-url="https://example.com/guide.xml"
```

由于这些播放列表主要由脚本处理,编辑时必须遵守以下几条规则:

- 所有文件必须使用 `.m3u` 扩展名
- 播放列表必须以 `#EXTM3U` 头开始
- 每条链接必须符合[直播流描述方案](./stream-description-scheme.md)
- 行尾必须使用 [CRLF](https://developer.mozilla.org/en-US/docs/Glossary/CRLF)
- 文件编码必须是不带 BOM 的 UTF-8

## 公开播放列表

与内部播放列表不同,这类播放列表是专门为普通用户生成的。

它们由 [playlist:generate](./scripts.md#playlistgenerate) 脚本每天在 UTC 00:00 自动生成,然后放入 [gh-pages](https://github.com/iptv-org/iptv/tree/gh-pages) 分支。

这些播放列表中的链接完全按照频道在我们[数据库](https://github.com/iptv-org/database)中的描述来组织。例如,某频道的播出区域标注为 `c/IT`,那么它的直播流链接就会被自动放入 `countries/it.m3u` 文件。

与内部播放列表的另一个区别是:公开播放列表中每个频道只保留基于画质和标签选出的最佳可用选项,`raw/` 文件夹中的播放列表除外。

此外,如果链接带有有效的[流 ID](./stream-id.md),描述中还会附上频道 Logo、分类、播出国家和语言。例如:

```
#EXTM3U x-tvg-url="https://example.com/guide.xml”
#EXTINF:-1 tvg-id="ExampleTV.us@SD” tvg-logo="https://example.com/logo.png” group-title="Movies”,Example TV (720p)
https://example.com/playlist.m3u8
```

公开播放列表的完整清单随时可以在 [PLAYLISTS.md](../PLAYLISTS.md) 中查看。
