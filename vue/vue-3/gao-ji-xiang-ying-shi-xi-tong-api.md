# 高级响应式系统 API

## customRef

`customRef` 用于自定义一个 `ref`，可以显式地控制依赖追踪和触发响应，接受一个工厂函数，两个参数分别是用于追踪的 `track` 与用于触发响应的 `trigger`，并返回一个一个带有 `get` 和 `set` 属性的对象。

使用自定义 ref 实现带防抖功能的 `v-model` ：

```markup
<!-- 省略基础结构 -->
<div id="app">
  <input v-model="text" type="text">
</div>

<script src="https://unpkg.com/vue@next"></script>
<script>
  const { createApp, customRef } = Vue
  const app = createApp({
    setup () {
      return {
        text: useDebouncedRef('hello world')
      }
    }
  })
  app.mount('#app')

  function useDebouncedRef (value, delay = 300) {
    let timeout
    return customRef((track, trigger) => ({
      get () {
        track()
        return value
      },
      set (newValue) {
        clearTimeout(timeout)
        timeout = setTimeout(() => {
          value = newValue
          trigger()
        }, delay)
      }
    }))
  }
</script>
```

## markRaw

显示标记一个对象**永远不会转换为响应式代理**，函数返回对象本身。

```javascript
const { markRaw, reactive, isReactive } from 'vue'
export default {
    setup () {
        const obj = markRaw({ a: 1 })
        const state = reactive(obj)

        console.log(isReactive(state.a)) // false
    }
}
```

