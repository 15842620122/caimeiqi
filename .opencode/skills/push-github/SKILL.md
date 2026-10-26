---
name: push-github
description: 提交项目并推送到 GitHub 远程仓库 https://github.com/15842620122/caimeiqi 。Use when the user says 推送到github、push到github、上传到github、github仓库、提交到github。
---

# 提交项目到 GitHub

将当前项目用 git commit 提交，并 push 到远程仓库 `https://github.com/15842620122/caimeiqi`（或 SSH 地址 `git@github.com:15842620122/caimeiqi.git`）。

## 步骤

1. 检查状态：
   - `git status --short` 和 `git status` 查看改动。
   - `git remote -v` 查看远程仓库：
     - 若已有 `github` remote，直接使用。
     - 若只有 `origin`（指向 Gitee），用 `git remote add github git@github.com:15842620122/caimeiqi.git` 添加新 remote（保留 Gitee 的 `origin` 不动）。
     - 若 `github` remote 已存在但地址不对，用 `git remote set-url github <url>` 修改。
   - `git branch --show-current` 确认当前分支（首次提交前默认 `master`）。

2. 暂存改动：
   - 默认 `git add -A` 暂存全部（本项目是静态站点，无构建产物）。
   - 若 `git status` 显示疑似密钥、token、大文件或用户明确不该提交的内容，先向用户确认再排除（用 `.gitignore` 或不 add）。

3. 提交：
   - 提交信息用中文简述本次改动，遵循仓库已有风格。
   - `git commit -m "<message>"`。
   - 若提交失败提示没有 user.name/user.email，先询问用户希望使用的姓名和邮箱，再 `git config user.name/user.email` 设置后重试；不要擅自编造。
   - 若仓库尚无任何提交，后续 push 使用 `-u` 建立跟踪。

4. 推送：
   - SSH 方式（推荐，公钥已配置）：`git push -u github <当前分支>`。
   - HTTPS 方式：`git push -u https://github.com/15842620122/caimeiqi.git <当前分支>`。
   - 若 push 因认证失败（401/SSH permission denied）：
     - SSH：用 `ssh -T git@github.com` 测试连通性，检查本地公钥是否已上传到 GitHub → Settings → SSH and GPG keys。
     - HTTPS：需要 Personal Access Token（PAT）作密码，不要在命令或配置中硬编码。
   - 若因远程有提交被拒绝，先 `git pull --rebase github <分支>` 处理后再 push；出现冲突则停下来向用户报告。

5. 完成后用 `git status` 和 `git log --oneline -3` 确认提交与推送结果，并向用户汇报。

## 注意

- 本仓库为纯静态 HTML/CSS/JS 项目，无构建、测试、lint 步骤。
- 当前仓库同时有两个远程：`origin` = Gitee，`github` = GitHub。推送时注意指定正确 remote 名称。
- 只做 commit/push，不要顺带重构或修改练习文件内容。
- 未经用户要求，不要 force push。
