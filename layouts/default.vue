<template>
  <div>
    <!-- 通过此组件来扩展应用的默认布局 -->
    <h1>layouts/default.vue 组件</h1>
    <!-- 别忘了在布局文件中添加 <nuxt /> 组件用于显示页面的主体内容 -->
    <nuxt />
    <!-- 因为默认布局的源码如下：
    ```html
    <template>
      <nuxt />
    </template>
    ``` -->
  </div>
</template>

<script>
// 一旦启用 layout default 布局，则全部页面都会应用这个布局
// 如果指向墨迹个页面启用某种布局，则不创建 defalut.vue，创建 foo.vue 然后在每个组件下配置 layout 即可
export default {
  name: 'LayoutDefault'
}
</script>

<style>

</style>