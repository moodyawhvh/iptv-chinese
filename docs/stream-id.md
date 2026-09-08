> 🌐 本文档由 [iptv-org/iptv](https://github.com/iptv-org/iptv) 翻译,英文原版见原项目。

# 流 ID

流 ID 是直播流的唯一标识符,由频道 ID 和信号源(feed)ID 组成,两者用 `@` 符号分隔。

```
ExampleTV.us@HD
```

## 频道 ID

这是频道的唯一 ID,由频道名称(去掉空格和特殊字符)后接国家代码构成,中间用句点分隔。

```
ExampleTV.us
```

## 信号源 ID

信号源 ID 就是信号源名称去掉所有空格和特殊字符后的结果。

它通常用于标示播出画质、时移、来源或播出地区,例如:

- HD
- Plus1
- Pluto
- WGTQ
- East
- MENA

所有频道 ID 和信号源 ID 的完整列表随时可以在 [iptv-org.github.io](https://iptv-org.github.io/) 查阅。

如果列表里缺少某个频道,可以随时通过这个[表单](https://github.com/iptv-org/database/issues/new?template=01_channels_add.yml)添加;同样,缺少的信号源也可以用这个[表单](https://github.com/iptv-org/database/issues/new?template=04_feeds_add.yml)添加。
