# 错误捕获收集

## 全局捕获 Promise 错误

### [unhandledrejection](https://developer.mozilla.org/zh-CN/docs/Web/API/Window/unhandledrejection_event)

 当[`Promise`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Promise) 被 reject 且没有 reject 处理器的时候，会触发 **`unhandledrejection`** 事件；这可能发生在 [`window`](https://developer.mozilla.org/zh-CN/docs/Web/API/Window) 下，但也可能发生在 [`Worker`](https://developer.mozilla.org/zh-CN/docs/Web/API/Worker) 中。 这对于调试回退错误处理非常有用。

```javascript
window.addEventListener('unhandledrejection', event => {
  console.warn(`UNHANDLED PROMISE REJECTION: ${event.reason}`)
})
```

 还可以使用 [`onunhandledrejection` ](https://developer.mozilla.org/en-US/docs/Web/API/WindowEventHandlers/onunhandledrejection) 事件处理程序属性来设置事件侦听器:

```javascript
window.onunhandledrejection = event => {
    console.warn(`UNHANDLED PROMISE REJECTION: ${event.reason}`)
}
```



