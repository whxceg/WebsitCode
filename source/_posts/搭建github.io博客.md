
---
title: 搭建github.io博客
---

### 一、Create a github Repository username.github.io 

### 二、搭建Hexo
#### 1、安装Node.js和Git
``` bash
sudo apt install -y nodejs npm
sudo apt install git
```
#### 2、安装Hexo
``` bash
sudo npm install hexo-cli -g
```
#### 3、创建hexo
``` bash
hexo init
npm install
hexo g
hexo s
```
#### 4、换个主题
``` bash
hexo clean #如果是安装第2个主题就不要写这句
git clone https://github.com/litten/hexo-theme-yilia.git themes/yilia
#现在找到_config.yml中的theme属性，改成yilia
hexo g
hexo s
```
### 三、将Hexo部署到github
找到根目录下一个叫“_config.yml ”的文件并打开它，翻到最后，添加以下代码并保存
``` bash
deploy:
  type: git #到"type"都是原来有的，添加后面的即可
  repo: git@github.com:name/name.github.io.git  #这里的"name"填你自己的
  branch: master
```
在Git Bash输入以下代码
``` bash
npm install hexo-deployer-git --save
cd ~/.ssh
ls #此时会显示一些文件,如果不存在id_rsa*之类的文件就不用备份
mkdir key_backup
cp id_rsa* key_backup
rm id_rsa* #以上三步为备份和移除原来的SSH key设置
ssh-keygen -t rsa -C "邮件地址@youremail.com" #生成新的key文件,邮箱地址填你的Github地址
#Enter file in which to save the key (/Users/your_user_directory/.ssh/id_rsa):<回车就好，当然也可以输入自己喜欢的名字>
#接下来会让你输入密码，然后会确认一遍，如果是Linux可能是隐形字
#上面的操作都成功之后会出现一个图，画的很拙劣，是表示OK了
```



进入Github首页，右上角头像旁边有个三角形，打开，里面有个“Settings”，点击“SSH and GPG keys"，再点击“New SSH key"
打开id_rsa.pub文件并复制里面的内容(删除末尾的邮箱)粘贴到github的key输入框内

测试下是否成功连接
``` bash
ssh -T git@github.com
```

设置账号和密码，输入以下代码
``` bash
git config --global user.name "username" #自己的名字，不一定非要是用户名
git config --global user.email "mail@mail.com" #github注册使用的邮箱
```

发布

``` bash
hexo d
```

写文章
在source/_posts文件夹下创建md文件编写内容，执行命令生成静态文件并发布
``` bash
hexo g
hexo d
```
