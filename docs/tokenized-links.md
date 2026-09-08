> 🌐 本文档由 [iptv-org/iptv](https://github.com/iptv-org/iptv) 翻译,英文原版见原项目。

# 令牌化链接

令牌化链接是包含一串由机器生成的唯一字符(即令牌,token)的个性化链接,用于授予 IPTV 直播流的访问权限。

示例:

- `https://example.com/index.m3u8?token=9f192891-eca5-2435-b9cb-147f376cdc1e`
- `https://example.com/index.m3u8?s=aWE0maGFzaF92YWx1`
- `https://example.com/index.m3u8?wmsAuthSign=c2bWU9Ni8yMC8yMDIVydmVyX3Rp2IDc6MDk6MjAgUmFsaWRtaWE0maGFzaF92YWx1ZTE5SkNSQkhqUG5JZVRRPT0md51dGVzPTMwJmlkPTZhMzZlNT1lRzlsZG4rOXYwZTIzNDk`

这类链接中的令牌会由服务提供方定期更新,因此链接往往在很短时间后就失效。

某些情况下,链接中还会包含一个 [UNIX 时间戳](https://en.wikipedia.org/wiki/Unix_time)格式的过期时间,准确指出链接何时失效:

`https://example.com/index.m3u8?token=2IDc6MDk6MjAgUmF&e=1813661332` _(`1813661332` => `2027-06-22T10:48:52.000Z`)_
