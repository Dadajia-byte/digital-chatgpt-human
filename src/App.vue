<template>
  <div class="container">
    <!-- 不需要单独的子元素来承载背景图像 -->
  </div>
</template>

<script>
export default {
  name: 'App',
  components: {}
}
</script>

<style scoped>
.container {
  width: 1440px;
  height: 1024px;
  background: url(./assets/Screenshot.png) -190px -147px no-repeat;
  background-size: 2082px 1171px;
  /* 或者 contain，根据需要选择适当的值 */
}</style>
