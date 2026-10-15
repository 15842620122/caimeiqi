---
name: commit-push
description: 提交项目并推送到 Gitee 远程仓库 https://gitee.com/cai-meiqiqi/caimeiqi2026。Use when the user says 提交项目、提交并推送、git commit、push、推送到 gitee/码云、上传到远程仓库.
---

# 提交项目到 Gitee

将当前项目用 git commit 提交，并 push 到远程仓库 `https://gitee.com/cai-meiqiqi/caimeiqi2026`。

## 步骤

1. 检查状态：
   - `git status --short` 和 `git status` 查看改动。
   - `git remote -v` 查看远程仓库；若为空或没有指向目标仓库，执行：
     `git remote add origin https://gitee.com/cai-meiqiqi/caimeiqi2026.git`
     （已存在其他 remote 名称时用 `git remote set-url origin <url>`。）
   - `git branch --show-current` 确认当前分支（首次提交前无分支时默认 `master`）。

2. 暂存改动：
   - 默认 `git add -A` 暂存全部（本项目是静态站点，无构建产物）。
   - 若 `git status` 显示疑似密钥、token、大文件或用户明确不该提交的内容，先向用户确认再排除（用 `.gitignore` 或不 add）。

3. 提交：
   - 提交信息用中文简述本次改动，遵循仓库已有风格（若无历史提交则用简洁描述，如 `初始提交：课程练习与首页`）。
   - `git commit -m "<message>"`。
   - 若提交失败提示没有 user.name/user.email，先询问用户希望使用的姓名和邮箱，再 `git config user.name/user.email` 设置后重试；不要擅自编造。
   - 若仓库尚无任何提交，后续 push 使用 `-u` 建立跟踪。

4. 推送：
   - `git push -u origin <当前分支>`（首次或无上游时加 `-u`）。
   - 若 push 因认证失败（401/提示输入用户名密码），告知用户需要 Gitee 账号凭据：可改用 SSH remote、配置凭据助手，或由用户手动输入；不要在命令或配置中硬编码密码。
   - 若因远程有提交被拒绝，先 `git pull --rebase origin <分支>` 处理后再 push；出现冲突则停下来向用户报告。

5. 完成后用 `git status` 和 `git log --oneline -3` 确认提交与推送结果，并向用户汇报。

## 注意

- 本仓库为纯静态 HTML/CSS 项目，无构建、测试、lint 步骤。
- 只做 commit/push，不要顺带重构或修改练习文件内容。
- 未经用户要求，不要 force push。
