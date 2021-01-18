<template>
  <div>
    <!-- 通过此组件来扩展应用的默认布局 -->
    <h1>layouts/foo.vue 组件</h1>
    <!-- 别忘了在布局文件中添加 <nuxt /> 组件用于显示页面的主体内容 -->
    <nuxt />
  </div>
</template>

<script>
export default {
  name: 'LayoutFoo'
}
</script>

<style>

</style>