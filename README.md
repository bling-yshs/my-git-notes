# 记录一些常见 Git 问题解决办法

1. git pull 发现需要选择分支 (branch)  
    `git branch --set-upstream-to=远程仓库分支(一般是origin/master或者origin/main) 本地分支(一般是master/main)` 具体可以 `git branch -a` 看一看，绿色是本地分支，红色是远程分支。
2. 更改远程仓库地址  
    `git remote set-url origin 远程分支地址`，记得再 `git pull` 一下。
3. 如何撤销 Github 的某次 commit (刚刚提交 Github 时候就遇到了，绝了)  
    `git reflog` 获取 commit ID (git 日志里前面几个英文字母的组合)，再 `git reset --hard commitID` 回退，最后 `git push origin HEAD --force` 进行强制推送。
4. 有点东西想加进刚刚的 commit，但是 commit 已经提交到 Github 了，怎么办？ <br>
    别停，**继续修改你的代码**，然后 `git commit --amend --no-edit` 进行commit替换，然后 `git push origin HEAD --force` 强制推送就行。