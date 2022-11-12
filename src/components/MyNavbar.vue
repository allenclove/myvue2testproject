<template>
    <div>
        <!-- 这里验证子传父，给这个按钮绑定一个点击方法handleLeft -->
        <button @click="handleLeft">left</button>
        navbar: {{ myname }}
        <button v-show="myright">right</button>
        <slot></slot>
    </div>
</template>
<script>
export default {
  // 当传递多个参数的时候，最好不要用以下注释的写法。因为这样没办法清晰的显示类型和设置默认值
//   props: ['myname', 'myright'],
  props: {
    myname: {
      type: String,
      default: ''
    },
    myright: {
      type: Boolean,
      default: true
    }
  },
  data () {
    return {

    }
  },
  methods: {
    handleLeft () {
      // 可以处理完逻辑之后就使用下面语句来触发父类引用当前标签设定的事件@event="handleEvent"
      this.$emit('event')
    }
  }
}
</script>
