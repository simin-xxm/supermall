<template>
  <div class="nav-bar">
    <div class="left">
      <slot name="left"></slot>
    </div>

    <div class="center">
      <slot name="center">购物街</slot>
    </div>
   <div class="right">
     <slot name="right"></slot>
   </div>
  </div>
</template>

<script>
  export default {
    name: "NavBar"
  }
</script>

<style scoped>
  .nav-bar{
    display: flex;
    /* 导航栏一般44px 状态栏20px */
    height: 44px;
    line-height: 44px;
    box-shadow: 0 1px 1px rgba(100,100,100,0.1);
  }
  .left , .right {width: 60px;}
  .center {flex: 1;text-align: center;line-height: 44px;}
</style>
