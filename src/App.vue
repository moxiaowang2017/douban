<template>
  <div id="app">

    <router-view></router-view>
  </div>
</template>

<script>
export default {
  name: 'app'
}
</script>

<style lang="scss">
  @import './style/common';
  #app{
    width: 100%;
    min-height:100%;
  }
</style>
