# 服务器配置git
## 安装git
  - yum install git
## 为操作系统添加用户和工作组
  - groupadd git
    - //添加git组
  - useradd -g git git
    - //新建git用户并添加到git组
  - passwd git
    - //为git用户设置密码
## 创建证书登录文件用来放置用户的公钥
  - cd /home/git
    - //git用户所在的目录
  - mkdir .ssh
    - //如果没有.ssh文件夹就创建它
  - touch .ssh/authorized_keys
    - //创建这个文件用来存公钥
  - chown git .ssh/authorized_keys
    - //将文件的拥有者改为git
  - chmod 600 .ssh/authorized_keys
    - //赋予拥有者以最大权限
## 创建git仓库目录
  - mkdir /home/gitrepo
    - //创建存放git仓库的目录
  - chown -R git /home/gitrepo
    - //将文件夹的拥有者改为git因为普通用户没有权限在其home目录外创建文件
  - cd /home/gitrepo
    - //进入该目录
  - git init --bare myProject.git
    - //创建名为myProject的git裸仓库（没有工作区文件只有commit）
  - git init www
    - //创建名为www的git非裸仓库（有工作区）
    - 非裸库服务器仓库需要执行
      ```
        git config receive.denyCurrentBranch ignore
      ```
      才可以push代码，每次提交代码到非裸库需要执行
      ```
        git reset --hard
      ```
        才可以看到提交的文件
  - 初始化完仓库执行
    - chown git myProject.git
      - //修改拥有者
    - chgrp git myProject.git
      - //修改用户组
  - 或
    - chgrp -R git /home/gitrepo/
      - //改变用户组，递归，最后执行方便
    - chown -R git /home/gitrepo/
      - //改变用户，递归，最后执行方便

## 克隆仓库
  - git clone git@yourserver:/home/gitrepo/myProject.git
    - //这里有必要解释一下 git clone 命令默认是ssh协议操作而ssh协议的默认端口是22建议用默认的22免得折腾搬瓦工默认修改了端口号可以自行去改回来
    - //该命令的完全形式为：git clone ssh://username@yourServer:Port/home/gitrepo/myProject.git
    - //自定义ssh端口：
      - vi /etc/ssh/sshd_config
        - //将其中的port 修改为你想要的端口号即可
## 添加本地key到服务器
  - cat ~/.ssh/id_rsa.pub | ssh git@yourServer 'cat - >> /home/git/.ssh/authorized_keys'
    - //使用这条命令可以将本地的公钥填入到主机的ssh验证文件内这样就使得本机克隆代码时不用再输入密码了。
    - //当然要使得这套机制生效还得修改/etc/ssh/sshd_config文件
    - //找到 #RSAAuthentication yes 和  #PubkeyAuthentication yes 以及#AuthorizedKeysFile      .ssh/authorized_keys 上的注释#去掉使配置生效
## 禁用git用户通过shell登录其只能使用git-shell
  - vi /etc/passwd
    - 将
      ```
        git:x:1000:1000::/home/git:/bin/bash
      ```
      改为
      ```
        git:x:1000:1000::/home/git:/usr/bin/git-shell
      ```
