### Git操作指南

1. Git的基本命令

   - 创建仓库

     | 命令                    | 说明            |
     | ----------------------- | --------------- |
     | git init                | 初始化仓库      |
     | git clone [git-address] | 拷贝远程Git仓库 |

   - 提交与修改

     | 命令                | 说明                           |
     | ------------------- | ------------------------------ |
     | git add [file-name] | 添加文件至暂存区               |
     | git status          | 查看本地仓库状态               |
     | git commit          | 提交暂存区文件至本地仓库       |
     | git diff            | 比较暂存区和本地仓库的文件差异 |
     | git reset           | 文件版本回退                   |
     | git rm              | 将文件从暂存区和本地仓库中删除 |
     | git mv              | 移动或重命名本地仓库文件       |

   - 日志管理

     | 命令                  | 说明                       |
     | --------------------- | -------------------------- |
     | git log               | 查看历史提交记录           |
     | git blame [file-name] | 查看指定文件的历史修改记录 |

   - 远程管理

     | 命令       | 说明                   |
     | ---------- | ---------------------- |
     | git remote | 远程仓库操作           |
     | git fetch  | 获取远程文件仓库       |
     | git pull   | 下载远程仓库文件并合并 |
     | git push   | 上传本地仓库文件并合并 |

2. Git的仓库创建

   - 选择本地仓库目录，使用`git init`命令将当前目录作为本地Git仓库；
   - 使用命令`git add [file-name]`将文件写入暂存区；
   - 使用命令`git commit -m [message]`将文件提交到本地Git仓库；

   ```
   $ git init [path-name]
   $ git add [file-name]
   $ git commmit -m [message]
   $ git branch -M main
   $ git remote add origin [git-address]
   $ git push -u origin main
   ```

3. Git的分支管理

   Git的分支是指向快照的一个指针，当进行新增或修改操作时可以通过派生一个分支来包含这些改变。这既阻止了不稳定的代码合入主代码分支，也提供了一个在合并进主分支之前清理提交历史记录的机会。

   ```
   创建分支：git branch [new-branch-name]
   切换分支：git checkout [new-branch-name]
   合并分支：git merge [branch-name]
   删除分支：git branch -d [branch-name]
   修改分支名称：git branch -M [new-branch-name]
   创建并切换分支：git checkout -b [new-branch-name]
   ```

4. Git的日志管理

   在使用Git提交了若干更新之后，又或者克隆了某个项目，想回顾下提交历史，我们可以使用日志命令查看。

   ```
   查看日志：git log [--oneline](简洁) [--graph](分支演化过程) [--reverse](逆向显示)
   [--author=user-name](指定作者日志) [--before={YYYY-MM-dd}](指定日期前日志) [--after={YYYY-MM-dd}](指定日期后日志)
   查看指定文件修改记录：git blame [file-name]
   ```