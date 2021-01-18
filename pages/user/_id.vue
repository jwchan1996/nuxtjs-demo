<template>
  <div class="user">
    <h1>User Page</h1>
    <p>{{ $route.params.id }}</p>
  </div>
</template>

<script>
export default {
  name: 'UserPage'
}
</script>

<style>

</style>