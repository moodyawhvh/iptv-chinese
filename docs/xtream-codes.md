> 🌐 本文档由 [iptv-org/iptv](https://github.com/iptv-org/iptv) 翻译,英文原版见原项目。

### Xtream Codes

大多数 Xtream Codes 直播流链接长这样:

`http(s)://{hostname}:{port}/{username}/{password}/{channelID}` _(端口通常是 `25461`)_

要确认一条链接是否指向 Xtream Codes 服务器,把 `hostname`、`port`、`username` 和 `password` 填入下面的 URL 格式,然后在浏览器中尝试打开:

`http(s)://{hostname}:{port}/panel_api.php?username={username}&password={password}`

如果页面返回了响应内容,就说明你面对的是一台 Xtream Codes 服务器。
