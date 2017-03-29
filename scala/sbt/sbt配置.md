# sbt 配置

## sbt 下载源配置
全局配置文件: `~/.sbt/repositories`  

```
[repositories]
  local

  aliyun-central: http://maven.aliyun.com/nexus/content/groups/public/

  #uk-maven : http://uk.maven.org/maven2
  maven-central: http://repo1.maven.org/maven2/
  #jcenter: http://jcenter.bintray.com/

  typesafe: http://repo.typesafe.com/typesafe/releases/
  #typesafe-snapshots: http://repo.typesafe.com/typesafe/snapshots/
  #sbt-plugin: http://dl.bintray.com/sbt/sbt-plugin-releases/
```

## sbt 依赖下载方式配置(可选)
sbt主要有两种下载依赖的方式  
### 一种是sbt自带  
其下载文件保存在`~/.ivy2/cache/`  
### 另一种是使用sbt插件[Coursier](https://github.com/alexarchambault/coursier)
其下载文件保存在`~/.coursier/cache/`  

全局使用coursier插件配置:
- 在`~/.sbt/0.13/plugins/build.sbt`中加入`addSbtPlugin("io.get-coursier" % "sbt-coursier" % "1.0.0-M14")`
- 关闭某项目中的coursier插件
参见 [sbt文档](http://www.scala-sbt.org/0.13/docs/zh-cn/Using-Plugins.html)  
example:
```
lazy val root = (project in file(".")).enablePlugins(PlayScala)
    .disablePlugins(CoursierPlugin)
```

## sbt 代理配置
sbt 代理配置作为jvm options 使用, example:  
```
sbt -Dsbt.override.build.repos=false -DsocksProxyHost=127.0.0.1 -DsocksProxyPort=7777 -Dhttp.proxyHost=127.0.0.1 -Dhttp.proxyPort=7777
```
具体参数则根据自己所使用的代理方式进行修改  
配置来源: [sbt doc](http://www.scala-sbt.org/0.13/docs/Proxy-Repositories.html)
在使用intellij idea时，sbt的配置在Preferences -> Build Tools -> SBT -> JVM Options