# vps搭建ss并加速
## 第一步
  - 安装centos-6-x86系统
  - 一键安装Shadowsocks Server
  - 打开Root shell - interactive，输入passwd，修改登录密码
## 第二步
  - ssh -l root -p SSH Port Ip  登录服务器
  - 安装kcptun
    - wget https://raw.githubusercontent.com/kuoruan/kcptun_installer/master/kcptun.sh
    - chmod +x ./kcptun.sh
    - ./kcptun.sh
      - 加速端口设置为443
## 第三步
  - 本地下载Shadowsocks客户端
    - [https://sourceforge.net/projects/shadowsocksgui/files/dist/](https://sourceforge.net/projects/shadowsocksgui/files/dist/)
  - 配置Shadowsocks
    ```
      地址: 127.0.0.1:443
      加密: aes-256-cfb
    ```
  - 本地下载kcptun客户端
    - [https://github.com/xtaci/kcptun/releases/tag/v20170315](https://github.com/xtaci/kcptun/releases/tag/v20170315) 达尔文386
  - 运行
    ```
      sudo ./client_darwin_386 -l 127.0.0.1:443 -r Ip:29900 -mode fast -key "your password”
    ```
