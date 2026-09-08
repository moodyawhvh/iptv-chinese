> 🌐 本文档由 [iptv-org/iptv](https://github.com/iptv-org/iptv) 翻译,英文原版见原项目。

# 工作流

为了自动化运行[脚本](./scripts.md),我们使用 [GitHub Actions 工作流](https://docs.github.com/en/actions/using-workflows)。

每个工作流都包含自己的一组脚本,可以手动触发,也可以在响应仓库事件时自动运行。

## check

每当有新的拉取请求开启时,依次运行 `api:load`、`playlist:lint` 和 `playlist:validate` 脚本;一旦检测到错误就会阻止合并。

## format

依次运行 `api:load`、`playlist:format`、`playlist:lint` 和 `playlist:validate` 脚本。

## update

每天 UTC 0:00 运行。依次执行 `api:load`、`playlist:update`、`playlist:lint`、`playlist:validate`、`playlist:generate`、`playlist:export` 和 `readme:update` 脚本,全部成功后自动部署更新后的文件。

## validate_issue

在 issue 被开启或编辑时运行。它使用 `issue:validate` 脚本检查请求是否存在错误,如果发现问题,机器人会把错误贴到评论中。

## validate_label

在 issue 被添加新标签时触发。它会检查该标签,如果不正确,机器人会删除它并留下评论说明原因。
