# 后端架构设计
- 接口、路由部分 `route`
- controller部分 `controller`
  - 处理请求
  - 回应请求
  - 调用业务操作 `operation.controller`
- 数据操作 `operation.model`
  - 数据库操作 `database operation`
  - 其他操作 `xxx operation`

# 项目目录结构
- `/src(app)`
    - `/controller`
        - 根据业务分controller子级目录 `extends BaseContoller`
            - 对应使用需要
            - 解析request
            - 权限管理
            - 调用`operation.controller` 传入请求参数`data: A`, 得到数据结果`Try[B]`
            - 处理operation返回值
    - `/operation`
        - `/business`
            - 与controller对应
            - 从使用需要->业务逻辑
        - `/module`
            - 对应业务逻辑模块
            - 尽量少冗余, 高复用
    - `/component`
        - `/basic`
            - `BaseController extends CustomException with Customlogger`
                - `.JsonResult`
                - `.JsonResultTryMatch`
                - `.JsonResultTryOptionMatch`
                - `...`
            - `/exception`
                - `CustomException`
                    - `.BusinessException` 正常流程, 业务异常, 出错信息需要反馈前端
                    - `.ServerException` 服务器错误, 添加日志, 返回500
                    - `.ExternException` 外部错误,
        - `/logger`
            - `Customlogger`
    - `/utility`

# 项目进度顺序
- 总体分析
    1. 接口分析文档 `demand doc` (需求文档)
    1. 接口route文档 `route doc` (需求文档->route文档)
    1. swagger api 源码 `route src` (route文档->api源码)
- 前端
    1. 使用api源码
- 后端
    1. `business model doc` 业务模块文档
    1. `controller doc` 接口对接业务文档(route->business)
    1. 数据库设计
    1. 完成业务模块(`operation.model`)以及对接模块(`operation.controller`)


### 总结
- 业务模块精简, 业务模块按照业务自身特性开放接口
- 接口部分冗余, 基本上与接口需求一一对应