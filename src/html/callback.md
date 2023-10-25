# 回调

在`yew`中可以使用`Callback::from`来创建回调事件。

## 在回调中使用异步函数

我们知道，`Callback::from`的使用方式如下：

```rust
fn example() {
    let on_click = {
        Callback::from(move |_:Event| {})
    };
}

```
在`Callback::from`中并不能直接使用异步函数，但是，我们可以借用`wasm-bindgen-futures`的`spawn_local`函数来使用异步函数。示例代码如下：

```rust
use wasm_bindgen_futures::spawn_local;

fn example() {
    let on_click = {
      Callback::from(move |_:Event| {
          spawn_local(async {
              let mut string = my_async_fn().await;
              string.push_str(", Yew");
          })
      })  
    };
}

async fn my_async_fn() -> String {
    String::from("Hello")
}
```
