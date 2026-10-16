# 仓库合并说明（2026-10-16）

| 原仓库 | 现仓库 |
|--------|--------|
| `duodoo-ai/duodoo-user-manual`（GitHub） | [**`duodoo-ai/extra-user-manual`**](https://github.com/duodoo-ai/extra-user-manual) |
| `duodoo-ai/zoodoo-user-manual`（Gitee，历史拼写） | [**`duodoo-ai/extra-user-manual`**](https://gitee.com/duodoo-ai/extra-user-manual) |

**本机路径**：`odoo18/extra-user-manual`（已删除 `odoo18/duodoo-user-manual`）。

**Remote（维护者）**：

| 名称 | URL |
|------|-----|
| `github` | `git@github.com:duodoo-ai/extra-user-manual.git` |
| `gitee` | `git@gitee.com:duodoo-ai/extra-user-manual.git` |

日常：`git push github master && git push gitee master`（`master` 可跟踪 `github/master` 或 `gitee/master` 任选其一）。

**专栏长文**仅使用目录 `17-专栏与发布长文/`（已删除废弃的 `16-母稿/`）。

**本目录**公开部分：DuodooTEKr 手册（10～17）。**PY 供水接口/部署文档涉密**，仅本机目录 + `.gitignore`，不进 Git。

旧克隆请改 remote：

```bash
git remote set-url origin git@github.com:duodoo-ai/extra-user-manual.git
git remote add gitee git@gitee.com:duodoo-ai/extra-user-manual.git   # 可选
```
