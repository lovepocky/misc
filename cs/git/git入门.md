# git使用入门

- git基本概念
    - `git` 是一个版本管理的工具
    - `git服务器` 是用于保存git工程的服务器, 常见的有`github`等
    - `git账号` 在某个具体的git服务器的用户账号
    - `git工程` 一个具体的用git工具进行版本管理的工程

- [追游git服务器](http://115.29.188.190/git/])

## 如何使用

### git 服务器账号使用
- git服务器验证用户身份的方式
    - https
    - ssh`推荐(https有上传大小限制; https每次需要输入密码或者保存密码在本地)`
        - 用户: 添加ssh公钥到git账号
        - 部署: 添加ssh公钥到相应git工程
        - [github文档:生成sshkey](https://help.github.com/articles/generating-an-ssh-key/)

### git 命令
- [Git教程- 廖雪峰的官方网站](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)