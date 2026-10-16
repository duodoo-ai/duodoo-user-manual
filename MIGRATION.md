# 仓库合并说明（2026-10-16）

| 原仓库 | 现仓库 |
|--------|--------|
| `duodoo-ai/duodoo-user-manual`（GitHub） | **`duodoo-ai/extra-user-manual`**（请在 GitHub **新建**或 **Rename** 旧仓） |
| `duodoo-ai/zoodoo-user-manual`（Gitee，历史拼写） | **`duodoo-ai/extra-user-manual`**（已推送 `master`） |

**本机路径**：`odoo18/extra-user-manual`（已删除 `odoo18/duodoo-user-manual`）。

**Remote（维护者）**：

| 名称 | URL | 用途 |
|------|-----|------|
| `gitee` | `git@gitee.com:duodoo-ai/extra-user-manual.git` | 主跟踪 `master` |
| `github` | `git@github.com:duodoo-ai/extra-user-manual.git` | 建仓后 `git push github master` |
| `github-duodoo` | `git@github.com:duodoo-ai/duodoo-user-manual.git` | 过渡：合并内容已推，可在 GitHub 将仓库 **Rename** 为 `extra-user-manual` 后删此 remote |
| `gitee-legacy` | `zoodoo-user-manual` | 可删 remote，历史已迁 |

**本目录** `odoo18/extra-user-manual` 为唯一维护入口，包含：

- DuodooTEKr 公开手册（10～17 编号目录）
- PY 供水系统接口与部署文档

旧克隆请改 remote：

```bash
git remote set-url origin git@github.com:duodoo-ai/extra-user-manual.git
git remote add gitee git@gitee.com:duodoo-ai/extra-user-manual.git   # 可选
```
