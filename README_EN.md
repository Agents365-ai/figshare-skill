# figshare-skill

> Claude Code / OpenClaw skill — search, download, create, and upload datasets via the Figshare v2 REST API.

One-stop Figshare skill covering public search, batch download, multi-part upload, and version publishing.

## Features

| Capability | figshare-skill | Native Claude Code |
|------------|----------------|--------------------|
| Public article search (`:title:`, `:author:`, ... operators) | ✅ | ❌ |
| Fetch by ID / DOI / URL and batch-download all files | ✅ | ❌ |
| List / create / update / publish your own articles | ✅ | ❌ |
| Manage Collections and Projects | ✅ | ❌ |
| 3-step (initiate → parts → complete) large-file upload | ✅ wrapped | ⚠️ manual |
| Create a new version of a published article | ✅ | ❌ |
| md5 / part sizing / retries handled | ✅ automatic | ❌ |

## Prerequisites

- `curl`, `jq`
- A [Figshare Personal Token](https://figshare.com/account/applications) for authenticated actions:

  ```bash
  export FIGSHARE_TOKEN=xxxxxxxxxxxx
  ```

## Install

### Claude Code

```bash
# global
git clone https://github.com/Agents365-ai/figshare-skill ~/.claude/skills/figshare-skill

# or per-project
git clone https://github.com/Agents365-ai/figshare-skill .claude/skills/figshare-skill
```

### OpenClaw

```bash
git clone https://github.com/Agents365-ai/figshare-skill ~/.openclaw/skills/figshare-skill
```

### SkillsMP

Search `figshare` on [skillsmp.com](https://skillsmp.com) to install.

## Usage

Trigger phrases: "search figshare", "download this figshare article", "upload my dataset to figshare", a figshare.com URL, or a `10.6084/m9.figshare.*` DOI.

```
> Search figshare for "single cell" datasets, top 10

> Download every file of https://figshare.com/articles/dataset/xxx/31957606 into ./data

> Upload ./results.zip to my draft article 31957803

> Publish a new version of article 12345678 with ./v2.csv
```

## Helper Scripts

| Script | Purpose |
|--------|---------|
| `scripts/upload.sh <article_id> <file>` | 3-step multi-part upload |
| `scripts/download.sh <id_or_url> [dir]` | Batch-download public article files |
| `scripts/new-version.sh <article_id> <file>` | Create and publish a new version |

## License

MIT — see [LICENSE](./LICENSE).
