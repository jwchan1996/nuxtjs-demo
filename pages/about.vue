<template>
  <div class="about">
    <h1>About Page</h1>

    <!-- a 链接，刷新导航，走服务端渲染 -->
    <h2>a 链接</h2>
    <a href="/">首页</a>

    <!-- routre-link 导航链接组件 -->
    <h2>router-link</h2>
    <router-link to="/">首页</router-link>

    <h2>编程式导航</h2>
    <button @click="toHome">首页</button>
  </div>
</template>

<script>
export default {
  name: 'AboutPage',
  methods: {
    toHome () {
      this.$router.push('/')
    }
  }
}
</script>

<style>

</style>