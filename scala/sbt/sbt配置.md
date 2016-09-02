# sbt 配置

## sbt 下载源配置
全局配置文件: `~/.sbt/repositories`  
以下是本人在 2016-09-02 所使用的内容，主要使用uk-maven镜像源下载

```
[repositories]
  local

  #oschina: http://maven.oschina.net/content/groups/public/
  #osc_central: http://maven.oschina.net/service/local/repositories/central/content
  #sonatype_public_grid: http://maven.oschina.net/service/local/repositories/sonatype-public-grid/content/
  #ibiblio: http://mirrors.ibiblio.org/pub/mirrors/maven2/
  #mvnrepository: http://maven.oschina.net/service/local/repositories/mvnrepository/content/

  #websudos: http://dl.bintray.com/websudos/oss-releases/
  uk-maven : http://uk.maven.org/maven2
  maven-central: http://repo1.maven.org/maven2/
  jcenter: http://jcenter.bintray.com/

  typesafe: http://repo.typesafe.com/typesafe/releases/
  typesafe-snapshots: http://repo.typesafe.com/typesafe/snapshots/
  typesafe-ivy-releases: http://repo.typesafe.com/typesafe/ivy-releases/, [organization]/[module]/[revision]/[type]s/[artifact](-[classifier]).[ext], bootOnly
  sbt-plugins-repo: http://repo.scala-sbt.org/scalasbt/sbt-plugin-releases/, [organization]/[module]/(scala_[scalaVersion]/)(sbt_[sbtVersion]/)[revision]/[type]s/[artifact](-[classifier]).[ext]
  sbt-plugin: http://dl.bintray.com/sbt/sbt-plugin-releases/
  typesafe-maven: http://repo.typesafe.com/typesafe/maven-releases/
  play: http://private-repo.typesafe.com/typesafe/maven-releases/

  sonatype-snapshots: http://oss.sonatype.org/content/repositories/snapshots
```

## sbt 依赖下载方式配置
sbt主要有两种下载依赖的方式  
一种是sbt自带  
其下载文件保存在`~/.ivy2/cache/`  
另一种是使用sbt插件[Coursier](https://github.com/alexarchambault/coursier)(推荐)   
其下载文件保存在`~/.coursier/cache/`  

全局使用coursier插件:
- 在`~/.sbt/0.13/plugins/build.sbt`中加入`addSbtPlugin("io.get-coursier" % "sbt-coursier" % "1.0.0-M14")`

## sbt 代理配置
sbt 代理配置作为jvm options 使用, example:  
```
sbt -Dsbt.override.build.repos=false -DsocksProxyHost=127.0.0.1 -DsocksProxyPort=1080 -Dhttp.proxyHost=127.0.0.1 -Dhttp.proxyPort=8118
```
具体参数则根据自己所使用的代理方式进行修改  
配置来源: [sbt doc](http://www.scala-sbt.org/0.13/docs/Proxy-Repositories.html)
