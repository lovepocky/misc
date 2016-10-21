# 关于写SwaggerUrl的一些经验

- 一个接口可以对应多个业务
- 一个接口可以有多个标签

- 一个接口只能有一个路由（或者说一个规则的路由）
- 一个接口只能有一个实现


因此接口的路由应该更贴近其实现，然后加上不同的业务标签

# 接口设计
example:
- `/`
    - `/web`
        - `/user`
        - `/market`
            - **`/goods`**
                - `/real`
                    - `/content`
                        - `/collection`
                - `/virtual`
        - `/staff`
            - `/manage`
                - **`/goods`**
                    - `/content`
                        - _get_
                        - _post_
                        - _put_
                        - _delete_
                        - `/collection`
                            - _get_
                    - **`/class`**
                        - _get_
                        - _post_
                        - _put_
                        - _delete_
                        - `/collection`
                            - _get_
    - `/app`

界定:
- 首先是定位到实体, 比如`/web/market/goods`
- 然后是实体的分类(如果有的话),`/web/market/goods/real`, `/web/market/goods/virtual`。
这里如果写成`/real/goods`和`/virtual/goods`的话,那么这就是不同的实体,而且`/real`和`/virtual`级是没有什么**get**之类的意义。
因此,这里分出的其实是goods分类下区别较大的2个分支,因此其content也出现分支。