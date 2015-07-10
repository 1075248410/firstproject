## 学习git第一天
语法
1. git add 文件 把文件添加到git仓库  
  例子：git add readme.txt  
  
2. git commit -m "说明" 提交到仓库 一次可以提交多个文件  
  例子： git commit -m "second"
  
3. git push "库名" master 把本地库推送到远程库上  
  git push learngit msater  
  
4. 从版本库中删除该文件，那就用命令git rm删掉，并且git commit：  
   git rm first.txt   
   git commit -m "remove first.txt"  
  