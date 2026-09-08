> 🌐 本文档由 [iptv-org/iptv](https://github.com/iptv-org/iptv) 翻译,英文原版见原项目。

# 贡献指南

- [简介](#introduction)
- [怎么做?](#how-to)
- [项目结构](#project-structure)

## 简介 <a id="introduction"></a>

**iptv-org** 不只是一个分享直播流链接的仓库。经过多年的投入与内容治理实践,它已经发展成为一个涵盖[频道](https://github.com/iptv-org/database)、[直播流](https://github.com/iptv-org/iptv)和[节目指南](https://github.com/iptv-org/epg)的知识库。为了让这些数据保持井然有序,我们必须遵循严格的结构要求,并为参与者设定一定的规范。

## 怎么做? <a id="how-to"></a>

### 如何向播放列表添加新的直播流链接?

你有以下几种选择:

1. 使用这个[表单](https://github.com/iptv-org/iptv/issues/new?assignees=&labels=streams:add&projects=&template=1_streams_add.yml&title=Add%3A+)创建新的请求,如果获得批准,该链接会在下次更新时自动加入播放列表。
2. 通过[拉取请求](https://github.com/iptv-org/iptv/pulls)直接把链接添加到播放列表。参见[播放列表](./docs/playlists.md)。

无论选择哪种方式,提交请求之前请先完成以下检查:

- 确保你使用的是有效的[流 ID](./docs/stream-id.md)。
- 确保该频道不在我们的黑名单中。最简单的确认方式是通过 [iptv-org.github.io](https://iptv-org.github.io/)。
- 通过[搜索](https://github.com/search?q=repo%3Aiptv-org%2Fiptv+http%3A%2F%2Fexample.com&type=code)仓库,确保该链接尚未存在于播放列表中。
- 确保你要添加的链接稳定且能正常工作。参见[直播流测试](./docs/stream-testing.md)。
- 确保该链接没有被[地域封锁](./docs/geo-blocking.md)。如果有,请在请求中注明。
- 确保该链接不是指向 [Xtream Codes](./docs/xtream-codes.md) 服务器。[为什么不接受 Xtream Codes 服务器的链接?](./FAQ.md#why-dont-you-accept-links-to-xtream-codes-servers)
- 确保该链接不是[令牌化链接](./docs/tokenized-links.md)。
- 确保链接直接指向广播源,没有多余的重定向。

如果广播只在特定国家可用,或者会周期性中断,请在请求中说明。

**重要:** 缺少有效流 ID 或无法工作的直播流链接的请求将被立即关闭。

### 如何修正直播流的描述信息?

直播流描述的大部分内容(频道名称、信号源名称、分类、语言、播出区域、Logo)都是通过流 ID 从 [iptv-org/database](https://github.com/iptv-org/database) 加载的。

因此,描述信息出错通常只有两种原因:

- **直播流的 ID 不正确:** 这种情况下,你只需通过这个[表单](https://github.com/iptv-org/iptv/issues/new?assignees=&labels=streams%3Aedit&projects=&template=2_streams_edit.yml&title=Edit%3A+)更新播放列表中的流 ID 即可。所有受支持频道及其对应 ID 的完整列表可以在 [iptv-org.github.io](https://iptv-org.github.io/) 上查看。
- **我们数据库中的频道信息有误:** 你可以在 [iptv-org.github.io](https://iptv-org.github.io/) 上核实。如果确实如此,请参考:[如何编辑数据库条目?](https://github.com/iptv-org/database/blob/master/CONTRIBUTING.md#how-to-edit-a-database-entry)。

变更获得批准后,直播流描述会在所有仓库中自动更新。

### 如何报告失效的直播流?

填写这个[表单](https://github.com/iptv-org/iptv/issues/new?assignees=&labels=streams:remove&projects=&template=3_streams_report.yml&title=Broken%3A+),一旦出现可用的替代源,我们会把它加入播放列表,或者至少先移除失效的链接。

发布报告之前,唯一要确认的是:

- 该链接仍在我们的播放列表中。你可以通过[搜索](https://github.com/search?q=repo%3Aiptv-org%2Fiptv+http%3A%2F%2Fexample.com&type=code)仓库来核实。
- 该链接是彻底失效,而不仅仅是被[地域封锁](https://en.wikipedia.org/wiki/Geo-blocking)。参见[直播流测试](./docs/stream-testing.md)。

**重要:** 缺少有效直播流链接的 issue 将被立即关闭。

### 如何将我的频道从播放列表中移除?

若要求从仓库中移除频道链接,请填写这个[表单](https://github.com/iptv-org/iptv/issues/new?assignees=&labels=removal+request&projects=&template=6_copyright-claim.yml&title=Remove%3A+)并等待请求审核(通常不到 1 个工作日)。获得批准后,该频道的链接会立即从仓库中移除。

同时,该频道会被加入我们的[黑名单](https://github.com/iptv-org/database/blob/master/data/blocklist.csv),以防止它日后再次出现在我们的播放列表中。

**重要:** 我们只接受频道所有者及其官方代表提交的移除请求,其他所有请求都将被立即关闭。

## 项目结构 <a id="project-structure"></a>

- `.github/`
  - `DISCUSSION_TEMPLATE/`:仓库的讨论模板。
  - `ISSUE_TEMPLATE/`:仓库的 issue 模板。
  - `workflows/`:[GitHub Actions](https://docs.github.com/en/actions/quickstart) 工作流。参见[工作流](./docs/workflows.md)。
  - `CODE_OF_CONDUCT.md`:行为准则——不想被封禁就别违反。
- `.readme/`
  - `preview.png`:`README.md` 中展示的图片。
  - `template.md`:`PLAYLISTS.md` 的模板配置。
- `scripts/`:仓库内部使用的工具脚本。参见[脚本](./docs/scripts.md)。
- `streams/`:包含所有直播流的内部播放列表。参见[播放列表结构](./docs/playlist-structure.md)。
- `tests/`:用于验证项目脚本的测试套件。
- `CONTRIBUTING.md`:你正在阅读的这个文件。
- `PLAYLISTS.md`:自动更新的可用播放列表清单。
- `README.md`:项目说明与文档总览。
