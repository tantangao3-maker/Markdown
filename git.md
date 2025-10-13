## ⚡️ 基础操作

```
# 初始化仓库
git init

# 克隆远程仓库
git clone <repo_url>

# 检查状态
git status

# 添加文件到暂存区
git add <file>          # 添加单个文件
git add .               # 添加所有修改

# 提交更改
git commit -m "提交信息"

# 查看提交历史
git log
git log --oneline       # 简洁版
git log --graph         # 分支图
```

## 🔄 远程操作

```
# 关联远程仓库
git remote add origin <repo_url>

# 推送到远程
git push -u origin <branch>   # 首次推送
git push                      # 后续推送

# 拉取远程更新
git pull origin <branch>

# 查看远程仓库
git remote -v
```

## 🌿 分支管理

```
# 创建分支
git branch <new_branch>

# 切换分支
git checkout <branch>
git switch <branch>          # (Git 2.23+)

# 创建并切换分支
git checkout -b <new_branch>
git switch -c <new_branch>   # (Git 2.23+)

# 合并分支
git merge <branch>

# 删除分支
git branch -d <branch>       # 安全删除
git branch -D <branch>       # 强制删除

# 查看分支
git branch                   # 本地分支
git branch -a                # 所有分支（含远程）
```

## ⚙️ 撤销与恢复

```
# 撤销工作区修改
git restore <file>           # (Git 2.23+)
git checkout -- <file>       # 传统写法

# 撤销暂存区文件
git restore --staged <file>  # (Git 2.23+)
git reset HEAD <file>        # 传统写法

# 修改最后一次提交
git commit --amend

# 重置到某个提交
git reset --soft <commit>    # 保留更改到暂存区
git reset --hard <commit>    # 丢弃所有更改
```

## 🏷️ 标签管理

```
# 创建标签
git tag <tag_name>           # 轻量标签
git tag -a <tag_name> -m "注释"  # 附注标签

# 推送标签到远程
git push origin <tag_name>
git push origin --tags       # 推送所有标签

# 删除标签
git tag -d <tag_name>
git push origin :refs/tags/<tag_name>  # 删除远程标签
```

## 🔄 变基操作

```
# 变基更新分支
git rebase <base_branch>

# 交互式变基（最近3次提交）
git rebase -i HEAD~3
```

## 🧪 贮藏更改

```
git stash                    # 贮藏当前修改
git stash pop                # 恢复最新贮藏
git stash list               # 查看贮藏列表
git stash apply stash@{n}    # 恢复指定贮藏
```

## 🧩 子模块管理

```
git submodule add <repo_url> <path>
git submodule update --init --recursive
```

## ⚠️ 紧急操作

```
# 强制覆盖本地分支
git fetch --all
git reset --hard origin/<branch>

# 恢复误删分支
git reflog                   # 查找提交哈希
git branch <branch> <commit_hash>
```
