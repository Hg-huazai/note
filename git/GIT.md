### 创建与合并分支

 1.例如创建dev分支

**-b：**表示创建并切换

```js
git checkout -b dev
```

2.查看当前分支(当前分支前面会标一个`*`号)

 git branch 会列出所有分支   

```js
git branch
```

3.然后正常操作，完成后提交到暂存区

```js
git add .
git commit -m'完成'
```

4.分支完成后，切回master分支(此时master分支上并没有dev分支上修改的内容，需要合并)

```js
git checkout master
```

5.把dev分支的工作成果**合并**到master分支上     这步要注意（后续有更改https://www.liaoxuefeng.com/wiki/896043488029600/900005860592480）

​	git merge命令用于合并指定分支到当前分支

```
git merge dev
```

6.合并成功后，就可以删除dev分支了

```
git branch -d dev
```

7.最新版本git提供了新的git  swich命令来切换分支

```

查看分支：git branch

创建分支：git branch <name>

切换分支：git checkout <name>或者git switch <name>

创建+切换分支：git checkout -b <name>或者git switch -c <name>

合并某分支到当前分支：git merge <name>

删除分支：git branch -d <name>
```

