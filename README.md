# figshare-skill

> Claude Code / OpenClaw 技能 — 通过 Figshare v2 REST API 搜索、下载、创建、上传学术数据集。

与 Figshare 交互的一体化技能：从公开检索到多分片上传，再到版本发布全部覆盖。

## 功能特性

| 能力 | figshare-skill | 原生 Claude Code |
|------|---------------|-----------------|
| 搜索公开文章（支持 `:title:` `:author:` 等字段） | ✅ | ❌ |
| 按 ID / DOI / URL 获取文章并批量下载 | ✅ | ❌ |
| 列出 / 创建 / 更新 / 发布个人文章 | ✅ | ❌ |
| 管理 Collections 与 Projects | ✅ | ❌ |
| 三步式（initiate → parts → complete）大文件上传 | ✅ 封装脚本 | ⚠️ 需手写 |
| 对已发布文章创建新版本 | ✅ | ❌ |
| md5 / 分片大小 / 断点处理 | ✅ 自动 | ❌ |

## 前置条件

- `curl`、`jq`
- 认证型操作需要 [Figshare Personal Token](https://figshare.com/account/applications)：

  ```bash
  export FIGSHARE_TOKEN=xxxxxxxxxxxx
  ```

## 安装

### Claude Code

```bash
# 全局
git clone https://github.com/Agents365-ai/figshare-skill ~/.claude/skills/figshare-skill

# 或项目级
git clone https://github.com/Agents365-ai/figshare-skill .claude/skills/figshare-skill
```

### OpenClaw

```bash
git clone https://github.com/Agents365-ai/figshare-skill ~/.openclaw/skills/figshare-skill
```

### SkillsMP

在 [skillsmp.com](https://skillsmp.com) 搜索 `figshare` 一键安装。

## 使用示例

触发短语：`搜索 figshare`、`下载这篇 figshare`、`把数据集上传到 figshare`、figshare.com 链接、`10.6084/m9.figshare.*` DOI 等。

```
> 在 figshare 上搜索 "single cell" 相关数据集，返回前 10 条

> 下载 https://figshare.com/articles/dataset/xxx/31957606 的全部文件到 ./data

> 把 ./results.zip 上传到我的草稿文章 31957803

> 为已发布文章 12345678 创建一个新版本，新文件是 ./v2.csv
```

## 辅助脚本

| 脚本 | 用途 |
|------|------|
| `scripts/upload.sh <article_id> <file>` | 三步式多分片上传 |
| `scripts/download.sh <id_or_url> [dir]` | 公开文章批量下载 |
| `scripts/new-version.sh <article_id> <file>` | 创建并发布新版本 |

## License

MIT — See [LICENSE](./LICENSE).

[English README](./README_EN.md)
