# 追游: 从零开始mac os开发环境搭建

## todo list

  - [ ] 整理常用软件安装包
  - [ ] 保存`~/.ivy2/cache`和`~/.coursier/`中常用的包, 便于新机子拷贝

1. ## 安装黑苹果系统
    - 硬件配置
        - 英特尔 第四代酷睿 i5-4590 @ 3.30GHz 四核
        - 主	板	华硕 B85M-F PLUS
        - 内	存	8 GB ( 金士顿 DDR3 1600MHz )
        - 硬	盘	ssd 256G
    - 安装过程
        - 已经制作好的`安装u盘`, 来源淘宝
        - 进BIOS, 配置UEFI启动参数选择操作系统为**其他操作系统**
        - 安装mac os到硬盘
            - 把u盘插到机箱后面的usb插口, 启动电脑
            - 选择安装osx到新的硬盘(如果没有显示新的硬盘则可能需要重新格式化硬盘,在安装标题栏的工具里面有磁盘工具)
            - 安装完之后启动到系统里
        - 配置EFI启动分区
            - 打开安装u盘
            - 打开`{U盘}/z/Clover Configurator.app`
            - 选择左侧栏`TOOLS`->`Mount EFI`
            - 选择右侧`Check Partition`, 找到EFI启动分区
            - 选择`Check Partition`旁边的`Mount EFI partition`, 将硬盘的EFI分区挂载, 此时可以在Finder中访问该分区
            - 复制`{U盘}/z/r3578/`目录下的2个文件`boot`和`EFI`到挂载的EFI分区根目录
            - 结束

    - mac os配置
        - 系统偏好设置
            使用Spotlight搜索, 或者屏幕左上苹果图标菜单中打开
            - 共享文件、远程登录
                - 系统设置/共享 -> 勾选文件共享和远程登录
            - 触摸板、键盘
                - 系统设置/键盘
                    - 按键重复和重复前延迟都调到最右端(快, 短)
                    - 修饰键调整
                        - 空格键左侧第一个键为`Command`
                        - 空格键左侧第二个键为`Option`
                - 系统设置/鼠标
                    - 滚动方向: 自然 `去掉勾选`
        - mac os常用快捷键参考
1. ## 安装常用软件
    - ShadowsocksX `必须`
        - [介绍](https://shadowsocks.com/)
        - [安装](https://github.com/shadowsocks/shadowsocks-iOS/wiki/Shadowsocks-for-OSX-Help)
        - 服务器配置: 用到的时候给
    - Homebrew `必须`
        - [介绍](http://brew.sh/)
        - 安装
            - homebrew

                ```
                /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
                ```
            - [brew-cask](https://ksmx.me/homebrew-cask-cli-workflow-to-install-mac-applications/)

                ```
                brew install brew-cask
                ```
    - istat menus `可选`
        - 介绍: 系统运行状态监测工具
        - 安装
    - shuttle + sshpass `可选`
        - 介绍: ssh 工具
        - 安装

            ```
            brew cask install shuttle
            ```
    - qq
    - chrome
        - 安装

            ```
            brew cask install google-chrome
            ```
    - 搜狗输入法
    - atom
1. ## 安装开发环境

    - Intellij IDEA `IDE`

    - git配置

    - scala
        - 安装
            - sbt: scala工程构建工具

                ```
                brew install sbt
                ```

                配置sbt环境: [sbt配置](../scala/sbt/sbt配置.md)
            - scala

                ```
                brew install scala
                ```
    - java
        - [安装](https://www.kancloud.cn/kancloud/ocds-guide-to-setting-up-mac/71035)

            ```
            brew cask install java
            ```

    - node.js
