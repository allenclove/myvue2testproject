<template>
    <div>
        mysidebar
        <ul>
            <li>11111111111111</li>
            <li>11111111111111</li>
            <li>11111111111111</li>
            <li>11111111111111</li>
            <li>11111111111111</li>
            <li>11111111111111</li>
        </ul>
    </div>
</template>
<!-- 【重要】组件的style标签最好加上scoped，声明成局部的css，否则可能会影响到或者被别人的全局css影响 -->
<style lang="scss" scoped>
// 这里上面使用lang="scss",就可以达到下面的效果：定义变量
$width:300px;
ul li{
  background-color: rgb(102, 186, 255);
  width: $width;
}
</style>
