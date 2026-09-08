> 🌐 本文档由 [iptv-org/iptv](https://github.com/iptv-org/iptv) 翻译,英文原版见原项目。

# 脚本

仓库内置了一些脚本,用于自动化日常流程,让维护工作轻松一点。

要运行这些脚本,你的电脑上必须安装 [Node.js](https://nodejs.org/en)。

- [act:check](#actcheck)
- [act:format](#actformat)
- [act:update](#actupdate)
- [act:validate_issue](#actvalidate_issue)
- [act:validate_label](#actvalidate_label)
- [api:load](#apiload)
- [issue:validate](#issuevalidate)
- [playlist:format](#playlistformat)
- [playlist:update](#playlistupdate)
- [playlist:generate](#playlistgenerate)
- [playlist:validate](#playlistvalidate)
- [playlist:lint](#playlistlint)
- [playlist:test](#playlisttest)
- [playlist:edit](#playlistedit)
- [playlist:export](#playlistexport)
- [readme:update](#readmeupdate)
- [report:create](#reportcreate)
- [lint](#lint)
- [test](#test)

## act:check

在本地运行 [check](./workflows.md#check) 工作流。依赖 [nektos/gh-act](https://github.com/nektos/gh-act)。

```sh
npm run act:check
```

## act:format

在本地运行 [format](./workflows.md#format) 工作流。依赖 [nektos/gh-act](https://github.com/nektos/gh-act)。

```sh
npm run act:format
```

## act:update

在本地运行 [update](./workflows.md#update) 工作流。依赖 [nektos/gh-act](https://github.com/nektos/gh-act)。

```sh
npm run act:update
```

## act:validate_issue

在本地运行 [validate_issue](./workflows.md#validate_issue) 工作流。依赖 [nektos/gh-act](https://github.com/nektos/gh-act)。

```sh
npm run act:validate_issue -- -e .github/mocks/events/issue_opened.json
```

## act:validate_label

在本地运行 [validate_label](./workflows.md#validate_label) 工作流。依赖 [nektos/gh-act](https://github.com/nektos/gh-act)。

```sh
npm run act:validate_label -- -e .github/mocks/events/issue_approved.json --actor Bob
```

## api:load

从 [iptv-org/api](https://github.com/iptv-org/api) 仓库下载最新的频道和直播流数据。

```sh
npm run api:load
```

## issue:validate

检查请求是否存在错误,如果发现问题,会把错误清单保存到文件 `temp/logs/errors.txt`

```sh
npm run issue:validate --body="### Stream URL..." --labels="streams:add"
```

## playlist:format

整理内部播放列表的格式,包括 [URL 规范化](https://en.wikipedia.org/wiki/URI_normalization)、去重、移除无效 ID,以及按频道名称、画质和标签排序。

```sh
# 整理 streams/ 目录下的所有播放列表
npm run playlist:format

# 整理指定的播放列表
npm run playlist:format path/to/playlist.m3u
```

## playlist:update

触发内部播放列表的更新,处理流程包括处理 issue 中已批准的请求。

```sh
npm run playlist:update
```

## playlist:generate

生成所有公开播放列表。

```sh
npm run playlist:generate
```

## playlist:validate

检查内部播放列表中的 ID 和链接是否有错误。

```sh
# 检查 streams/ 目录下的所有播放列表
npm run playlist:validate

# 检查指定的播放列表
npm run playlist:validate path/to/playlist.m3u
```

## playlist:lint

检查内部播放列表是否存在语法错误。

```sh
# 检查 streams/ 目录下的所有播放列表
npm run playlist:lint

# 检查指定的播放列表
npm run playlist:lint path/to/playlist.m3u
```

## playlist:test

测试内部播放列表中的链接。

```sh
# 检查 streams/ 目录下的所有播放列表
npm run playlist:test

# 检查指定的播放列表
npm run playlist:test path/to/playlist.m3u
```

该命令会自动检测播放列表中所有链接的状态并逐一显示:

```sh
npm run playlist:test streams/fr.m3u

streams/fr.m3u
┌─────┬───────────────────────────┬──────────────────────────────────────────────────────────────────────────────────────────────────────┬────────────────┬───────────────────────────┐
│     │ tvg-id                    │ url                                                                                                  │ label          │ status                    │
├─────┼───────────────────────────┼──────────────────────────────────────────────────────────────────────────────────────────────────────┼────────────────┼───────────────────────────┤
│  0  │ 6ter.fr                   │ https://origin-caf900c010ea8046.live.6cloud.fr/out/v1/29c7a579af3348b48230f76cd75699a5/dash_short... │                │ LOADING...                │
│  1  │ 20MinutesTV.fr            │ https://lives.digiteka.com/stream/86d3e867-a272-496b-8412-f59aa0104771/index.m3u8                    │                │ FFMPEG_STREAMS_NOT_FOUND  │
│  2  │                           │ https://video1.getstreamhosting.com:1936/8420/8420/playlist.m3u8                                     │                │ OK                        │
│  3  │ ADNTVPlus.fr              │ https://samsunguk-adn-samsung-fre-qfrlc.amagi.tv/playlist/samsunguk-adn-samsung-fre/playlist.m3u8    │ Geo-blocked    │ HTTP_FORBIDDEN            │
│  4  │ Africa24.fr               │ https://edge12.vedge.infomaniak.com/livecast/ik:africa24/manifest.m3u8                               │                │ OK                        │
│  5  │ Africa24English.fr        │ https://edge17.vedge.infomaniak.com/livecast/ik:africa24sport/manifest.m3u8                          │                │ OK                        │
│  6  │ AfricanewsEnglish.fr      │ https://37c774660687468c821a51190046facf.mediatailor.us-east-1.amazonaws.com/v1/master/04fd913bb2... │                │ HTTP_GATEWAY_TIMEOUT      │
│  7  │ AlpedHuezTV.fr            │ https://edge.vedge.infomaniak.com/livecast/ik:adhtv/chunklist.m3u8                                   │ Not 24/7       │ HTTP_NOT_FOUND            │
```

另外,如果在命令后加上 `--fix` 选项,脚本会自动把它检测到的所有失效直播流从你本地的播放列表副本中移除:

```sh
npm run playlist:test streams/fr.m3u -- --fix
```

## playlist:edit

用于快速映射直播流的小工具。

```sh
npm run playlist:edit path/to/playlist.m3u
```

## playlist:export

为 [iptv-org/api](https://github.com/iptv-org/api) 仓库生成包含所有直播流的 JSON 文件。

```sh
npm run playlist:export
```

## readme:update

更新 [PLAYLISTS.md](PLAYLISTS.md) 中的配置和可用播放列表清单。

```sh
npm run readme:update
```

## report:create

生成当前 issue 状况的报告。

```sh
npm run report:create
```

## lint

检查工具脚本本身的语法错误。

```sh
npm run lint
```

## test

运行上述所有脚本的测试。

```sh
npm test
```
