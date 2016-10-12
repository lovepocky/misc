# 关于写SwaggerUrl的一些经验

- 一个接口可以对应多个业务
- 一个接口可以有多个标签

- 一个接口只能有一个路由（或者说一个规则的路由）
- 一个接口只能有一个实现


因此接口的路由应该更贴近其实现，然后加上不同的业务标签