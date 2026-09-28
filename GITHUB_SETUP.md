# GitHub 配置说明

当前目录已初始化为 `main` 分支的本地 Git 仓库，并包含：

- `.github/workflows/validate-plugin.yml`：在 push 和 pull request 时校验清单、技能 YAML 头和 TODO 占位符；
- `.github/ISSUE_TEMPLATE/research-gap.yml`：用来记录市场分析证据缺口；
- `.agents/plugins/marketplace.json`：供仓库 marketplace 使用的插件目录；
- `README.md`、`LICENSE` 和 `.gitignore`。

由于用户没有提供 GitHub 组织、仓库名或远程 URL，本次没有替用户创建远程仓库、添加 remote 或推送代码。准备发布到 GitHub 时，在仓库根目录执行：

```text
git add .
git commit -m "build market strategy guidance plugin"
git remote add origin https://github.com/<OWNER>/<REPOSITORY>.git
git push -u origin main
```

在 Codex 中从 GitHub marketplace 添加时，可使用：

```text
codex plugin marketplace add https://github.com/<OWNER>/<REPOSITORY>.git --sparse .agents/plugins
```

发布前请替换 `plugin.json` 中的作者、仓库、网站、隐私政策和服务条款信息，并检查 GitHub Actions 通过。
