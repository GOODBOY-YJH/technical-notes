1. 本地初始化一个 Git 仓库
在已有的文件夹下，打开 git bash，git 仓库初始化命令：git init

或者通过新建一个本地文件夹， git 命令：git init [文件夹名]

git 初始化不会清空当前文件夹的数据，只是在文件夹中添加一个 .git 文件，用于存储一些git 数据

2. 添加、 提交文件
git add . ：添加所有的文件暂存

git commit -m "注释" ：将暂存区的内容提交到仓库

3. 在 github 上新建一个仓库，复制仓库的链接。
注意，新建的时候暂时不需要勾选创建 README 的文件

4. 绑定远程仓库
git remote add origin "仓库链接" ：绑定本地与远程仓库

5. 将本地文件，推送到远程仓库
git push -u origin master ：推送本地文件至 github

git push -u origin master -f ：强制推送本地文件至 github