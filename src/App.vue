<template>
  <div id="app">
    记录一下组件的基本用法
    <!-- 可以看到组件由三部分组成：<template> <script> <style> -->
    <br>
    <img src="/favicon.ico">
    你好啊！{{ myname }}
    <br>
    <!-- 值得注意的是，传递参数的时候，如果要传递布尔值，则需要在前面加个冒号，否则传递的是字符串 -->
    <!-- 这里设置@event="handleEvent"，当子组件发起事件触发handleEvent方法 -->
    <my-navbar myname="cyc2022" :myright="false" @event="handleEvent">
    <div>这个是插槽的使用</div>
    </my-navbar>
    <input type="text" v-model="mytext">
    <button @click="handleAdd">提交</button>
    <ul>
      <li v-for="data in datalist" :key="data">
        {{data}}
      </li>
    </ul>
    <br>
    <my-sidebar v-show="isShow"></my-sidebar>
  </div>
</template>
<script>
// import Vue from 'vue'
// 导入组件使用：1. 首先使用import导入组件
import myNavbar from './components/MyNavbar'
import MySidebar from './components/MySidebar'

// 2. 【全局写法】然后还需要在vue中注册，才能使用
// Vue.component('myNavbar', mynavbar)
export default {
  // 注意这里的data的写法， 函数式写法，然后里面一个return接大括号
  data () {
    return {
      myname: 'cyc',
      mytext: '',
      datalist: [],
      isShow: true
    }
  },
  // 【局部写法】在组件内部注册
  components: {
    myNavbar,
    MySidebar
  },
  methods: {
    handleAdd () {
      this.datalist.push(this.mytext)
      this.mytext = ''
    },
    handleEvent () {
      // 由事件触发的方法，这里就是子传父的一种方式
      this.isShow = !this.isShow
    }
  }
}
</script>
<!-- 【重要】组件的style标签最好加上scoped，声明成局部的css，否则可能会影响到或者被别人的全局css影响 -->
<style lang="scss" scoped>
// 这里上面使用lang="scss",就可以达到下面的效果：定义变量
$width:300px;
ul li{
  background-color: yellow;
  width: $width;
}
</style>
