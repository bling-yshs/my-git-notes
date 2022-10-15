
# 记录一些常见 Git 问题解决办法

## 老 Github 仓库默认分支是 master，新的是 main，请注意区分，下方一律用 master

- git pull 发现需要选择分支 (branch)
  - `git branch --set-upstream-to=远程仓库分支(一般是origin/master) 本地分支(一般是master)` 具体可以 `git branch -a` 看一看，绿色是本地分支，红色是远程分支。

- 更改远程仓库地址并一键修复BUG
  - `git remote set-url origin 新的远程仓库地址 && git fetch -p && git pull && git reset --hard origin/master`

- 如何撤销 Github 的某次 commit (刚刚提交 Github 时候就遇到了，绝了)
  - `git reflog` 获取 commit ID (git 日志里前面几个英文字母的组合)，再 `git reset --hard commitID` 回退，最后 `git push origin HEAD --force` 进行强制推送。

- 有点东西想加进刚刚的 commit，但是 commit 已经提交到 Github 了，怎么办？
  - 别停，**继续修改你的代码**，然后 `git commit --amend --no-edit` 进行 commit 修改，然后 `git push origin HEAD --force` 强制推送就行。

- 刚刚 commit 留的信息不小心留错了，而且交到 Github 了，该怎么改呢？
  - `git commit --amend` 改完再 `git push origin HEAD --force` 强制推送。

- 不小心删了从 Github 上 Clone 的项目的某个文件/文件夹，该怎么恢复呢？
  - 需要提前保存好修改过的代码，然后 `git reset --hard origin/master`
  
- 报错解决三连：  
   `git config --global --unset http.proxy`  
   `git config --global http.sslVerify false`

- 回退一个commit：
  - `git reset --hard HEAD^`
  