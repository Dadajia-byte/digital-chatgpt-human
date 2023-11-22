<template>
  <div class="container">
    <!-- 不需要单独的子元素来承载背景图像 -->
    <GroupA class="groupA"/>
  </div>
</template>

<script>
import GroupA from './components/GroupA'
export default {
  name: 'App',
  components: {GroupA}
}
</script>

<style scoped>

.container {
  position: relative;
  width: 1440px;
  height: 1024px;
  background: url(./assets/Screenshot.png) -190px -147px no-repeat;
  background-size: 2082px 1171px;
  /* 或者 contain，根据需要选择适当的值 */
}

.groupA {
  position: absolute;
  width: 477px;
  height: 82px;
  top: 911px;
  left: 901px;
  border-radius: 10px;
  border: 1px
    }
</style>
