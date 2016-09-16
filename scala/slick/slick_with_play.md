# slick with play framework

## todo list
- 一些坑
  - [complete] play reload 过多时会造成'Too Many Connections', 导致无法连接上数据库


## 问题解决
- ### play reload 过多时会造成'Too Many Connections', 导致无法连接上数据库
  - 原因  
工程使用的db声明在某object中，全局都使用者一个db，
当play application reload 时没有进行 `db.close()`，导致没有释放connection，
在重复多次reload之后使得数据库无法连接
  - 解决方案  
reference
    - [Play doc 2.5.x](https://www.playframework.com/documentation/2.5.x/PluginsToModules)  

    具体步骤：


1. 新建play application的`ApplicationLifecycle`的hook task  
  example:

  ```
  package task
  /**
    * Created by lovepocky on 16/9/12.
    */
  import scala.concurrent.Future
  import javax.inject._

  import play.api.inject.ApplicationLifecycle
  import utility.database.DBTools
  import utility.logger.CustomLogger

  trait ApplicationLifeTask

  @Singleton
  class ApplicationLifeTaskImpl @Inject()(lifecycle: ApplicationLifecycle) extends CustomLogger with ApplicationLifeTask {

      loggers.console.debug("ApplicationLifeTask Creating")

      lifecycle.addStopHook { () =>
          Future.successful {
              loggers.console.debug("ApplicationLifeTask Stopping")
              loggers.console.info("Closing Slick DB")
              DBTools.caishengu_db.close()
          }
      }
  }
  ```

  其中utility中的DBTools和CustomLogger为工程相关部分
1. 新建play module  
  example：

  ```
    package task

    import play.api.{Configuration, Environment}
    import play.api.inject.{Binding, Module}
    import utility.logger.CustomLogger

    /**
      * Created by lovepocky on 16/9/12.
      */
    class ApplicationLifeTaskModule extends Module with CustomLogger {
        override def bindings(environment: Environment, configuration: Configuration): Seq[Binding[_]] = {
            loggers.console.info("ApplicationLifeTaskModule Start Configuring")
            Seq(
                bind[ApplicationLifeTask].to[ApplicationLifeTaskImpl].eagerly()
            )
        }

    }
  ```
1. 启用上一步中的module  
  添加
  `play.modules.enabled += "task.ApplicationLifeTaskModule"`到`application.conf`
