# gitstudy
This is study git demo  <br>
学习git练习  <br>

#####创建版本库
  * git add -A                  // 加入暂存区
  * git commit -m "说明"         // 提交到历史版本
  * git push origin master      //再推送到远程

######小结：
    * 初始化一个Git仓库，使用git init命令。
    * 添加文件到Git仓库，分两步：
        * 第一步，使用命令git add <file>，注意，可反复多次使用，添加多个文件；
        * 第二步，使用命令git commit，完成。
    * 每次修改，如果不add到暂存区，那就不会加入到commit中。

#####查看仓库当前状态
  * git status

######小结：
    * 要随时掌握工作区的状态，使用git status命令。

#####查看修改内容
  * git diff 文件名
  * git diff HEAD --文件名     //查看工作区与版本库里面最新版本的区别

######小结：
    * 如果git status告诉你有文件被修改过，用git diff可以查看修改内容。

#####版本回退  <br>
  * git reset --hard HEAD^  //回到上一个版本
  * git reset --hard commit id(版本号)  //回到某个版本
  * 上一个版本就是HEAD^，上上一个版本就是HEAD^^，往上100个版本 HEAD~100

######小结：
    * HEAD指向的版本就是当前版本，因此，Git允许我们在版本的历史之间穿梭，使用命令git reset --hard commit_id。
    * 穿梭前，用git log可以查看提交历史，以便确定要回退到哪个版本。
    * 要重返未来，用git reflog查看命令历史，以便确定要回到未来的哪个版本。

#####查看提交历史
  * git log

#####查看命令历史
  * git reflog

#####工作区与暂存区
  * Git的版本库里存了很多东西，其中最重要的就是称为stage（或者叫index）的暂存区，还有Git为我们自动创建的第一个分支master，以及指向master的一个指针叫HEAD。
  * 把文件往Git版本库里添加的时候，是分两步执行的：
    * 第一步是用git add把文件添加进去，实际上就是把文件修改添加到暂存区；
    * 第二步是用git commit提交更改，实际上就是把暂存区的所有内容提交到当前分支。
  * 因为我们创建Git版本库时，Git自动为我们创建了唯一一个master分支，所以，现在，git commit就是往master分支上提交更改。
  * 可以简单理解为，需要提交的文件修改通通放到暂存区，然后，一次性提交暂存区的所有修改。

#####撤销修改
  * git checkout -- file  //可以丢弃工作区的修改：
  * 命令git checkout -- file 意思就是，把file文件在工作区的修改全部撤销，这里有两种情况：
    * 一种是file自修改后还没有被放到暂存区，现在，撤销修改就回到和版本库一模一样的状态；
    * 一种是file已经添加到暂存区后，又作了修改，现在，撤销修改就回到添加到暂存区后的状态。
  * 总之，就是让这个文件回到最近一次git commit或git add时的状态。
  * __git checkout -- file命令中的--很重要，没有--，就变成了“切换到另一个分支”的命令__。
  * 如果修改完后git add 到暂存区，但是在git commit，可以用git reset HEAD file把暂存区的修改撤销掉，重新放回工作区。
  * 用git reset HEAD file 后再用git checkout -- file 可以丢弃掉工作区的修改。
  * git reset命令既可以回退版本，也可以把暂存区的修改回退到工作区。当我们用HEAD时，表示最新的版本。
  * 当改错了东西，还从暂存区提交到了版本库时，可以用*版本回退*回退到上一个版本。前提是还没有把本地版本推送到远程。

######小结：
    * 场景1：当改乱了工作区某个文件的内容，想直接丢弃工作区的修改时，用命令git checkout -- file。
    * 场景2：当不但改乱了工作区某个文件的内容，还添加到了暂存区时，想丢弃修改，分两步，第一步用命令git reset HEAD file，就回到了场景1，第二步按场景1操作。
    * 场景3：已经提交了不合适的修改到版本库时，想要撤销本次提交，用版本回退，不过前提是没有推送到远程库。

</br>
</br>
</br>
</br>
</br>
原文：[git 廖雪峰](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/)