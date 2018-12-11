## Git快速入门
### 创建Github账号、仓库
略

### 生成SSH公私钥
1. 通过命令`ssh-keygen`命令生成`id-rsa`、`id-rsa.pub`私钥、公钥文件，上传github公钥文件完成绑定
（注：默认linux此时存储`/.ssh`目录下，windows存储在`MsysGit`包下，ssh连接将自动校验密钥文件）
2. 登陆github获取ssh地址，在终端中使用如下命令连接。将不再需要账号密码验证
```
git remote set-url origin someaccount@github.com/someaccount/someproject.git
```

### Git本地版本管理
1. 工作目录下通过`git init`声明目录使用git进行版本管理
2. 如果需要，可以克隆远程仓库到本地
```
git clone https://github.com/someaccount/someproject.git
```
3. `Coding...`（无论你使用终端还是图形IDE）
4. 提交更改，对于新增文件要先键入版本控制，一般则需要提交本地仓库暂存
```
#添加版本控制
git add file1 file2 ...
#快速添加控制
git add .
#提交本地暂存
git commit -m 'comments'
```
5. 回滚更改，回滚误操作到检出/初始/最新版本
```
git reset --hard HEAD
```

### Git异地协同管理
假设多人同时pull一个仓库，并且你们完成了本地的检出  
1. 查看本地与远程仓库差异
```
git fetch
```
2. 从远程更新本地仓库
```
git pull origin <branch name>
```
3. 推送本地更新到远程
```
#先检查本地更改提交
git add .
git commit -m 'comments'
#推送本地仓库内容
git push origin <branch name>
```
注：考虑异地开发交互同步，建议先更新后提交