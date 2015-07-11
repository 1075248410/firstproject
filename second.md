## 学习git第二天  
### 1.创建版本库  
   什么是版本库呢？版本库又名仓库，英文名repository，你可以简单理解成一个目录，这个目录里面的所有
文件都可以被Git管理起来，每个文件的修改、删除，Git都能跟踪，以便任何时刻都可以追踪历史，或者在
将来某个时刻可以“还原”。  
  
所以，创建一个版本库非常简单，首先，选择一个合适的地方，创建一个空目录  
`mkdir learngit`  
`cd learngit`  
`pwd`  
`pwd` 命令用于显示当前目录  
  
如果你使用Windows系统，为了避免遇到各种莫名其妙的问题，请确保目录名（包括父目录）不包含中文。  
第二步，通过`git init`命令把这个目录变成Git可以管理的仓库：  
  
` git init `  
  `Initialized empty Git repository in /Users/michael/learngit/.git/`  
    
  瞬间Git就把仓库建好了，而且告诉你是一个空的仓库（empty Git repository），
  细心的读者可以发现当前目录下多了一个`.git`的目录，这个目录是Git来跟踪管理版本库的，没事千万不要手动修改这个目录里面的文件，不然改乱了，就把Git仓库给破坏了。
  如果你没有看到.git目录，那是因为这个目录默认是隐藏的，用`ls -ah`命令就可以看见。  
  
  `git status`命令可以让我们时刻掌握仓库当前的状态， 告诉你有文件被修改过   
  `git diff readme.txt`  查看修改内容  
  
### 2.版本回退
  `git log`命令显示从最近到最远的提交日志，  
  如果嫌输出信息太多，看得眼花缭乱的，可以试试加上`--pretty=oneline`参数：  
    
  首先，Git必须知道当前版本是哪个版本，在Git中，用HEAD表示当前版本，也就是最新的提交3628164.
  ..882e1e0（注意我的提交ID和你的肯定不一样），上一个版本就是HEAD^，上上一个版本就是HEAD^^，
  当然往上100个版本写100个^比较容易数不过来，所以写成HEAD~100。  
  
  现在，我们要把当前版本“append GPL”回退到上一个版本“add distributed”，就可以使用git reset命令：
  `git reset --hard HEAD^`  
  `--hard`参数有啥意义？这个后面再讲，现在你先放心使用。  
  
  现在，你回退到了某个版本，关掉了电脑，第二天早上就后悔了，想恢复到新版本怎么办？
  找不到新版本的commit id怎么办？  
  在Git中，总是有后悔药可以吃的。当你用`git reset --hard HEAD^`回退到`add distributed`版本时，
  再想恢复到append GPL，就必须找到append GPL的commit id。Git提供了一个命令`git reflog`用来记录
  你的每一次命令：  
  要重返未来，用`git reflog`查看命令历史，以便确定要回到未来的哪个版本。  
####小结
  * HEAD指向的版本就是当前版本，因此，Git允许我们在版本的历史之间穿梭，使用命令git reset --hard commit_id。  
  * 穿梭前，用git log可以查看提交历史，以便确定要回退到哪个版本。  
  * 要重返未来，用git reflog查看命令历史，以便确定要回到未来的哪个版本。  
    