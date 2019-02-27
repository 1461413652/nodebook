:wq 返回

### 添加，提交，查看修改内容
1. 把要添加的东西文件放在mkdir创建出来的文件目录里，或者子目录
2. git add test.txt  添加到仓库，可以写多个add,再commit
3. git commit -m "提交说明"
4. git status 查看仓库的状态（要随时使用status查看工作环境）
5. git diff 查看修改内容
6. alt + f8 清除窗口
7. git log 查看历史记录   git log --pretty=oneline整理的
8. cat filename 查看文件内容
  
---
### 删除文件

```
git checkout -- file  恢复误删除的文件

git rm file  删除文件 再提交 git commit -m ""


git rm cc -r -f  删除文件
```

---

### 版本回退

1、HEAD回退
```
git log 查看提交记录  git log --pretty=oneline整理的


git reset --hard HEAD^ 返回上一个版本，上上一个版本就是HEAD^^，当然往上100个版本写100个^比较容易数不过来，所以写成HEAD~100
```
2、提交ID回退

```
git reset --hard 4549104ff79af8460c7797ac86c15e6669fefe23
```
3、关电脑以后，找不到id的情况

```
git reflog 查看每次的命令的id，然后 git reset --hard id就可以了
```

---

### 工作区和暂存区
 所有的add都会放在暂存区，然后commit的时候才是提交,提交到当前分支，提交只会提交暂存区里的，没放入暂存区，不会被提交  




```
git diff HEAD -- filename   查看工作区和库里的区别
```
---

### 撤销修改

```
git checkout -- readme.txt

情景1：未添加到暂存区
git checkout -- readme.txt 撤销修改文件

情景2：已添加到暂存区
git reset HEAD readme.txt  撤销暂存区的修改文件
git checkout -- readme.txt

情景3：
提交了，commit ,只能用版本回退了  
但是修改单个文件，可以用git reset HEAD^ readme.txt命令把上一版本中的readme.txt文件重新置入缓存区，再提交或用checkout到工作去修改
```
---
### 分支

```
查看分支：git branch  当前分支前面会标一个*号

创建分支：git branch <name>

切换分支：git checkout <name>

git checkout -b dev  创建分支，并切换到创建的分支上


合并某分支到当前分支：git merge <name>


合并分支，禁止快速模式，会生成一个commit  git merge --no-ff -m "merge with no-ff" dev


删除分支：git branch -d <name>

git branch -D <naem> 在没合并以前，强行删除分支
```
##### 解决分支冲突（相当于两人同时更改冲突了）
比如我在次分支上操作然后提交了，然后在主分支上也操作提交了，最后在主分支上合并次分支的时候，就会冲突。gitstatus会告诉我们冲突的文件。 必须解决了再提交

##### bug分支
当你接到一个修复一个代号101的bug的任务时，很自然地，你想创建一个分支issue-101来修复它，但是，等等，当前正在dev上进行的工作还没有提交，所以需要把当前的分支藏起来，再去操作处理bug的分支

```
git stash  隐藏当前分支，git status查看工作区是干净的就可以了

首先确定要在哪个分支上修复bug，假定需要在master分支上修复，就从master创建临时分支
修复bug

修复完成后，切换到master分支，并完成合并，最后删除处理bug的分支

接着回到原来的分支干活，git stash list查看隐藏的

git stash pop 恢复隐藏的
```





  


