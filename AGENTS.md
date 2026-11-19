# 给 Agent 的说明

## 仓库角色

本仓库是用 Quartz 5 生成的公开网站，也是一个独立 Git 仓库。公开笔记放在 `content/`，来自私人知识库中用户指定的子集。

知识库里的 `光学/笔记.md` 对应这里的 `content/光学/笔记.md`。两份文件的字节内容保持一致。要改公开笔记的文字或目录，改知识库原稿，再由用户决定是否同步。不在本仓库里直接改这些副本。

## 本机不构建

页面由 GitHub Actions 构建。`.github/workflows/deploy.yml` 在 `v5` 分支收到推送后运行。构建使用仓库里的 `quartz/`、`package.json`、`package-lock.json` 和 `quartz.config.default.yaml`。这些文件保留。

本机不需要安装 Node.js。不运行 `npm i`、`npx quartz create` 或 `npx quartz build`。

`quartz.config.default.yaml` 里的 `baseUrl` 是 `junlibb.github.io/technical_blog`。推送完成后查看 `https://junlibb.github.io/technical_blog/`。构建失败时查看该次 Actions 日志。

`docs/`、上游测试和 changeset 是 Quartz 的开发资料。用户没有要求时不删除。

## 哪些文件属于站点

`blog-owned.txt` 列出同步时保留的 `content/` 路径，目前有 `index.md`。点开头的文件也保留，例如 `content/.gitkeep`。

`content/双目深度计算.md` 已经在博客里，知识库的 `published.txt` 还没有这条路径。同步检查会把它列进删除列表。用户确认要保留之前，不执行同步写入。要继续公开这篇笔记，先在知识库里用 `publish-note` 把它写入清单。

## 仓库位置

知识库与本仓库默认同级，目录名是 `knowledge` 和 `technical_blog`。位置不同时使用用户给出的路径。

发布单篇笔记使用技能 `publish-note`。按清单更新内容和目录使用技能 `sync-published`。技能来自个人技能仓库的用户级链接，仓库本身可以放在其他位置。当前对话里看不到技能时，向用户询问技能仓库的位置。

用户没有要求发布或同步时，不复制、不覆盖、不删除 `content/` 里的笔记。提交和推送需要用户另外确认。站点更新要推到 `v5`。
