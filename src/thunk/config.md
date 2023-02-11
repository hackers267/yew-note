# 配置文件

`Thunk`的配置文件是`Thunk.toml`。

## Serve 字段

通过`serve`字段，可以配置`Thunk`启动的服务器的设置。
* `address`  服务器地址
* `port`     服务器端口
* `open`     启动成功后可否自动打开浏览器
* `no_autoreload`  是否自动加载浏览器重新加载

示例:
```toml Trunk.toml
[serve]
address = "0.0.0.0"
port= "8000"
open = false
no_autoreload = true
```

## proxy 字段

可以通过`proxy`设置开发时的代理。通过使用`[[proxy]]`可以设置多个代理，其选项如下：

* backend: 代理后的接口地址
* rewrite: 需要代理的接口的规则
* ws:  是否代理ws
* insecure:  是否启用`https`

示例：
```toml Trunk.toml
[[proxy]]
backend = "http://localhost:3000"
rewrite = "/api"

[[proxy]]
backend = "http://localhost:3000"
rewrite = "/custom_api"
insecure = true
```
