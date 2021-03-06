## native 与 js 

---
### WKWebview 与 js
**WKScriptMessageHandler, WKUIDelegate, WKNavigationDelegate**
- WKNavigationDelegate 

`负责webpage的加载与跳转`


- WKUIDelegate
  
`遵守该协议，用来实现webpage行为对应的native UI展示`

- WKScriptMessageHandler
  
  `遵守该协议的类提供一个用于接受来自webpage中js执行传递的信息`

  ``` Swift
  /** @abstract Adds a script message handler.
     @param scriptMessageHandler The message handler to add.
     @param name The name of the message handler.
     @discussion Adding a scriptMessageHandler adds a function
     window.webkit.messageHandlers.<name>.postMessage(<messageBody>) for all
     frames.
     */
    open func add(_ scriptMessageHandler: WKScriptMessageHandler, name: String)
  ```

  `通过给WKWebViewConfiguration.userViewcontroller增加不同的‘name’来实现不同的js函数调用`


### Javascriptcore
> JSContext 是 JS 执行上下文，你可以把它理解为 JS 运行的环境
> 
> JSValue 是对 JavaScript 值的引用，任何 JS 中的值都可以被包装为一个 JSValue
> 
> JSVirtualMachine 表示 JavaScript 执行的独立环境
> 
> JSManagedValue 是对 JSValue 的包装，加入了“conditional retain”
> 
> JSExport 协议 -> 实现将 Objective-C 类及其实例方法，类方法和属性导出为 JavaScript 代码的协议


#### JSPatch
基于runtime，进行方法替换

#### Weex & react native
基于jscore，达到js执行原生方法


### 参考
- [WKWebView使用JS与Swift交互](https://tomoya92.github.io/2018/07/05/swift-webview-javascript/)
- [WKWebView基本使用](https://juejin.im/post/5a3123dc6fb9a045104a7def)
- [深入剖析 iOS 与 JS 交互](https://zhuanlan.zhihu.com/p/31368159)
- [JSPatch 实现原理详解](https://github.com/bang590/JSPatch/wiki/JSPatch-%E5%AE%9E%E7%8E%B0%E5%8E%9F%E7%90%86%E8%AF%A6%E8%A7%A3)