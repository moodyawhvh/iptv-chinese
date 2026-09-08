<div align="center">

# IPTV 中文文档

[![原项目](https://img.shields.io/badge/原项目-iptv--org--iptv-blue?style=flat-square&logo=github)](https://github.com/iptv-org/iptv)
[![GitHub Stars](https://img.shields.io/github/stars/iptv-org/iptv?style=flat-square&label=原项目Stars)](https://github.com/iptv-org/iptv/stargazers)
[![微信联系](https://img.shields.io/badge/微信-uaycar-brightgreen?style=flat-square&logo=wechat)](#)

</div>

> 本文档是 [iptv-org/iptv](https://github.com/iptv-org/iptv) 官方 README 的中文翻译,仅供学习参考;如有出入请以英文原文为准。

**代部署 / 定制服务 / 技术咨询 请添加微信:uaycar**

---

## 📖 项目简介

iptv-org/iptv 收集了来自世界各地、公开可用的 IPTV(网络协议电视)频道,并整理成标准 m3u 播放列表。仓库通过 GitHub Actions 定时自动更新,频道元数据由社区在独立数据库仓库中持续维护与校对,是目前全球最有影响力的开源直播频道列表合集之一。

## 📋 目录

- 🚀 如何使用
- 📺 播放列表
- 🗓 EPG(电子节目指南)
- 🗄 数据库
- 👨‍💻 API
- 📚 资源
- 💬 讨论区
- ❓ FAQ
- 🛠 参与贡献
- ⚖ 法律声明
- © 许可证

## 🚀 如何使用?

把任意一个播放列表链接,粘贴进任意支持直播流的视频播放器(如 VLC、PotPlayer 等),然后按下「打开 / 播放」即可观看。

播放器推荐清单见 awesome-iptv 仓库的 apps 章节。

## 📺 播放列表

收录仓库内全部频道的主播放列表地址:

```
https://iptv-org.github.io/iptv/index.m3u
```

除主列表外,仓库还按四种维度提供拆分列表(完整清单见原仓库 PLAYLISTS.md 文件),常用入口如下:

| 维度 | 链接格式 | 示例 |
|:-----|:-----|:-----|
| 按国家 | https://iptv-org.github.io/iptv/countries/&lt;国家代码&gt;.m3u | https://iptv-org.github.io/iptv/countries/cn.m3u(中国频道) |
| 按语言 | https://iptv-org.github.io/iptv/languages/&lt;语言代码&gt;.m3u | https://iptv-org.github.io/iptv/languages/zho.m3u(中文频道) |
| 按类别 | https://iptv-org.github.io/iptv/categories/&lt;类别名&gt;.m3u | https://iptv-org.github.io/iptv/categories/news.m3u(新闻频道) |
| 按地区 | https://iptv-org.github.io/iptv/regions/&lt;地区名&gt;.m3u | https://iptv-org.github.io/iptv/regions/asia.m3u(亚洲频道) |

也可以使用分组合并列表,一次订阅一整组:`index.country.m3u`(按国家分组)、`index.language.m3u`(按语言分组)、`index.category.m3u`(按类别分组)、`index.region.m3u`(按地区分组)。

> 注:频道是否可看取决于源站,部分链接可能随时间失效,请以仓库自动更新后的最新列表为准。

## 🗓 EPG(电子节目指南)

大部分频道的电子节目指南(EPG)可通过 iptv-org/epg 仓库发布的工具下载使用,常用节目单地址:

```
https://iptv-org.github.io/epg/index.xml.gz
```

## 🗄 数据库

所有频道数据均来自 iptv-org/database 仓库。如果发现频道信息有误,请到该仓库提交 issue 反馈。

## 👨‍💻 API

官方提供公开 API,文档见 iptv-org/api 仓库,可用于查询频道与播放列表数据,方便二次开发与自建服务。

## 📚 资源

更多与 IPTV 相关的实用资源(播放器、工具、社区项目等),见 iptv-org/awesome-iptv 仓库。

## 💬 讨论区

有问题或想法,欢迎到 iptv-org 组织的 Discussions 参与讨论。

## ❓ FAQ

常见问题的答案见原仓库 FAQ.md 文件,涵盖播放器选择、频道无法播放、EPG 配置等高频问题。

## 🛠 参与贡献

提交 issue 或 pull request 前,请先阅读原仓库 CONTRIBUTING.md 贡献指南。感谢所有已经做出贡献的开发者与赞助者!

## ⚖ 法律声明

本仓库不存储任何视频文件,仅收录用户提交的、指向公开可用视频流 URL 的链接;据我们所知,这些内容均由版权所有者有意公开。如果播放列表中的任何链接侵犯了你的版权,可通过原仓库的 issue 模板提交版权申诉要求移除。但请注意:仓库对链接指向的内容没有控制权,仅从播放列表移除链接,并不会让内容从互联网上消失。提供链接本身并不直接构成版权侵权,因为链接提供方并未复制任何内容,因此这不是向 GitHub 发送 DMCA 通知的有效理由。要彻底移除相关内容,应联系真正托管该内容的主机服务商(而不是 GitHub,也不是本仓库维护者)。

## © 许可证

本项目以 CC0 1.0(公共领域贡献)许可发布,仓库内的播放列表可自由使用,无需署名。

---

> 本文档为 [iptv-org/iptv](https://github.com/iptv-org/iptv) 官方 README 的中文翻译版本,所有代码版权归原项目作者所有,遵循其原始许可证(CC0)。

**代部署 / 定制服务 / 技术咨询 请添加微信:uaycar**

**如果觉得有用,请给原项目点个 Star!** ⭐
