# git基础

## 基本Linux命令

- cd：改变目录
- cd . .：回退上一个目录，直接cd进入默认目录
- pwd：显示当前所在目录路径
- ls（ll）：都是列出当前目录中的所有文件，只不过ll列出的内容更为详细
- touch：新建一个文件，如touch index.js，就会在当前目录下新建一个index.js文件
- rm：删除一个文件
- mkdir：新建一个目录，就是新建一个文件夹
- rm -r：删除一个文件夹，切勿使用rm -rf/，是格式化
- mv：移动文件，mv index.html src，index.html是我们要移动的文件，src是目标文件夹，需要保证文件和目标文件夹在同一目录下  
- reset：重新初始化终端，清屏
- clear：清屏
- history：查看命令历史
- help：帮助
- exit：退出
- #表示注释

## 新建仓库

- git init
- git clone：从远程仓库克隆一个

![](C:\Users\lenovo\Desktop\学习进阶\git\git图片\git1.PNG)

![](C:\Users\lenovo\Desktop\学习进阶\git\git图片\git2.PNG)

## 工作区域

- 包括工作区，暂存区，本地仓库
- 用git add加入暂存区，git commit加入仓库

- git四种状态：

![](C:\Users\lenovo\Desktop\学习进阶\git\git图片\git四种状态.PNG)

## 添加和提交文件

- git init：创建仓库
- git status：查看仓库的状态
- git add：添加到暂存区
- git commit：提交，只会提交暂存区的文件

![](git图片/git提交1.PNG)

![](git图片/git提交2.PNG)

![](git图片/git提交3.PNG)

- git status:查看当前仓库状态
- code+文件能用vscode创建一个文件
- ls能查看当前目录下的文件
- cat+文件能查看文件内容
- git status下的文件为红色说明处于未跟踪状态
- 当add后文件为黄色
- git commit -m " ~"：-m后要有参数，提交暂存区的文件到仓库
- add *.txt：能提交所有文件后缀为txt的文件
- add . ：能提交文件夹下的所有文件
- git log:查看文件提交的信息
- git log --oneline:查看文件提交的简略信息

## 回退版本

- git reset
- git reset --soft:回退到某一版本，并且保留工作区和暂存区的内容
- git reset --hard:回退某一版本，并且丢弃工作区和暂存区所有内容
- git reset --mixed：只保留工作区的内容，丢弃暂存区，是reset命令的默认参数

![](git图片/回退版本1.PNG)

![](git图片/回退版本2.PNG)

- cp -rf 复制文件且重命名为
- git log --oneline能查看版本号
- 回退版本后要加上版本号
- ls是查看工作区文件
- HEAD^代表回退到上一个版本
- git ls-files是查看暂存区文件
- git reflog能查看自己的操作历史和版本号，能回退到之前的操作

## 查看差异

- git diff
- 用于查看工作区、暂存区、本地仓库之间的差异
- 查看不同版本之间的差异
- 查看不同分支之间的差异

![](git图片/差异1.PNG)

![](git图片/差异2.PNG)

![](git图片/差异3.PNG)

- git diff输出：第一行为变更的文件，后面为修改内容，红色为删除内容，绿色为刚添加的内容，比较的是工作区和暂存区的内容
- git diff HEAD比较工作区和版本库的差异
- git diff --cached比较暂存区和版本库的差异
- 在diff后面加上两个版本的提交id能比较两个版本
- 用HEAD能表示最新提交
- HEAD~,HEAD^为上一版本
- HEAD~2为上两个版本
- 后面再加文件名为比较这特定文件的差异

## 删除文件

- rm file;git add file:先从工作区删除文件，然后在暂存区删除内容
- git rm file把工作区和暂存区同时删除
- git rm --cached file:把文件从暂存区删除，但保留在当前工作区
- git rm -r*:递归删除某个目录下的所有子目录和文件
- 删除后不要忘记提交到仓库

![](git图片/删除1.PNG)

![](git图片/删除2.PNG)

## gitignore

- 作用：忽略掉一些不应该被加入到版本库中的文件，使得仓库更小更干净
- 忽略文件：系统或者软件自动生成的文件，编译产生的中间文件和结果文件，运行时生成的日志文件，缓存文件，临时文件，涉及身份、密码、口令、秘钥等敏感信息文件
- 比如.class文件，.o文件，.env文件，.zip和tar文件，.pem文件



- 文件的匹配规则
- 空行或者以#开头的行会被git忽略，一般空行用于可读性的分隔，#一般用作注释
- 使用标准的Blob模式匹配，例如：星号*通配任意个字符，问号？匹配单个字符，中括号[]表示匹配列表中的单个字符，比如[abc]表示a/b/c
- 两个星号**表示匹配任意的中间目录
- 中括号可以使用短中线连接，比如：[0-9]表示任意一位数字，[a-z]表示任意一位小写字母
- 感叹号！表示取反 

![](git图片/忽略1.PNG)

![](git图片/忽略2.PNG)

![](git图片/忽略3.PNG)

![](git图片/忽略4.PNG)

![](git图片/忽略5.PNG)

![](git图片/忽略6.PNG)

- 添加到.gitignore后用status就看不见添加进的文件
- 添加到版本库中access.log被忽略无法加入，而other.log会被加入
- 用*.log能通配所有以log结尾的文件，在.gitignore修改添加
- 两个>>表示追加到文件的后面
- git rm会把文件从工作区和暂存区同时删除，加上--cached能不删除本地文件
- git默认不会将空的文件夹加入仓库
- git status -s表示查看状态的简略模式
- 两个问号第一个表示暂存区的状态，第二个表示工作区
- 在.gitignore中添加temp/

## 同步远程仓库

- 利用push和pull
- git clone repo-address：克隆仓库
- git push <remote><branch>推送更新内容
- git pull<remote>拉取更新内容

![](git图片/拉取远程仓库.PNG)

- git remote add <shortname> <url>添加一个远程仓库
- git remote -v：查看当前仓库和远程仓库的别名和地址
- git branch -M main:指定分支的名称为main
- git push -u origin main:main把本地仓库和别名为origin的仓库关联起来，把本地仓库的main分支和远程仓库的main分支关联起来
- git pull origin main:main，可以省略为git pull，拉取远程仓库的内容

gitee和gitlab也是代码托管平台

## 分支

- git branch：查看分支列表
- git branch branch-name：创建分支
- git checkout branch-name：切换分支
- git switch branch-name：切换分支
- git merge branch-name：合并分支
- git branch -d branch-name：删除分支（已合并）
- git branch -D branch-name：删除分支（未合并）

![](git图片/分支1.PNG)

![](git图片/分支2.PNG)

![](git图片/分支3.PNG)

![](git图片/分支4.PNG)

## 合并冲突

- 两个分支未修改同一个文件的同一处位置：git自动合并
- 两个分支修改了同一个文件的同一处位置：产生冲突
- 解决方法：
	- 手工修改冲突文件，合并冲突内容
	- 添加暂存区
	- 提交修改
- 中止冲突：当不想继续执行合并操作时可以使用 git merge --abort来中止合并过程

![](git图片/合并冲突1.PNG)

![](git图片/合并冲突2.PNG)

## rebase

- git rebase branch-name

![](git图片/回退1.PNG)

- merge：优点：不会破坏原分支的提交历史，方便回溯和查看。缺点：会产生额外的提交节点，分支图比较复杂
- rebase：优点：不会新增额外的提交记录，形成线性历史，比较直观和干净。缺点：会改变提交历史，改变了当前分支branch out的节点。避免在共享分支使用
- 一般不会在公共的分支上使用rebase操作

- 版本号规则：
	- 主版本：主要的功能变化或重大更新
	- 次版本：一些新的功能、改进和更新，通常不会影响现有功能
	- 修订版本：一些小的bug修复、安全漏洞补丁等，通常不会更改现有的功能和接口

