<template>
  <div class="container">
    <nuxt-link to="/" tag="h1" class="error" >404 Page not Found</nuxt-link>
  </div>
</template>

<script>
export default {
    layout : 'dark'
}
</script>

<style>
.error{
    cursor: pointer;
    text-align: center;
}
</style>