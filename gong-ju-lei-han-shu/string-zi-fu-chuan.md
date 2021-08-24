---
description: 记录一些实用的字符串操作方法及技巧。
---

# string 字符串

## 获取随机字符串

利用 `Math.random()` 和 `Number.prototype.toString()` 方法实现获取随机字符串。

[`Number`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Number) 对象覆盖了 [`Object`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object) 对象上的 `toString()` 方法，它不是继承的 [`Object.prototype.toString()`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/toString)。对于 [`Number`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Number) 对象，`toString()` 方法以指定的基数返回该对象的字符串表示。

如果转换的基数大于10，则会使用字母来表示大于9的数字，比如基数为16的情况，则使用a到f的字母来表示10到15。

如果基数没有指定，则使用 10。  


```javascript
Math.random().toString(32).slice(2)
```

