# TodoMVC App

## 下载模板

```bash
$ git clone https://github.com/tastejs/todomvc-app-template.git todomvc
$ cd todomvc
$ npm install
```

### 引入 browser-sync 作为 http 服务工具

安装 browser-sync

```bash
$ npm install --save-dev browser-sync
```

配置 package.json 中的 scirpts 字段

```json
"scripts": {
  "dev": "browser-sync start --server --files \"index.html, js/*.js\""
}
```

启动开发服务

```bash
$ npm run dev
```

## 计算属性、过滤器、方法总结

- methods 方法
  + 使用场景：需要有事件处理函数
  + 也可以在 Mustache 插值表达式位置使用
  + 虽然支持，但是更建议当在 Mustache 中使用方法的时候都定位为计算属性
- filters 过滤器
  + 使用场景：处理文本格式化，例如日期格式化
  + 使用注意：内部无法访问 this 实例，也就无法处理 data 中的数据
- computed 计算属性
  + 使用场景：获取业务数据，自带缓存
  + 特性：本质是方法，但是必须当做属性来使用
  + 不是方法，使用的时候无法传参

计算属性对比方法而言，如果多次使用，则计算属性效率要高于方法。

## 自定义指令总结

> 什么时候需要自定义指令？
> 当不可避免需要操作 DOM 的时候尽量选择自定义指令。

但是能通过 MVVM 解决的视图问题，尽量不要操作 DOM。

## 注册自定义指定

实例选项的 `directives` 选项用来注册指令。
该选项是一个对象，对象的 key 就是自定义指令的名字。
key 对应的 value 是一个对象：用来配置指令的生命钩子。

### 指令的生命钩子

- bind   指令与元素第一次绑定的时候使用
- inserted 元素插入到 DOM 之后才执行
- update   指令所在模板更新的时候调用
- componentUpdated 指令所在模板更新完成的时候调用
- unbind 指令与元素解绑的时候调用

不同的钩子有不同的场景，例如只需要指令执行一次的话就使用 bind 或者 inserted
而如果需要指令随着 DOM 模板更新而重复调用，则使用 update 或者 componentUpdated。

### 生命钩子参数

- el       获取作用指令的 DOM 元素
- binding  获取指令的相关数据，这里最终的是 value 属性可以拿到指令的值

## 在 HTML 元素上使用自定义指令

- 指令的名字
- 可以在 DOM 模板中为指令传值

## 学习框架的一些经验

- 过文档
- 做业务
- 先解决业务问题
- API 不可能全部都用上
- 但是对于简单的 API 可以都记录一下
- 对于复杂抽象不懂得 API 先有个印象，随着对框架使用的经验越来越丰富才能接触更广阔的领域。
- 千万不要纠结于某个小点
- 接触的过程中再慢慢的了解底层原理
- 一开始能搞懂的原理的更好，搞不懂的先把规则玩儿明白

- 每天一点点

- API
- 解决业务问题
- 搞原理
