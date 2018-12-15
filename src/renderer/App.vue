<template>
  <div id="app">
    <router-view></router-view>
  </div>
</template>

<script>
export default {
  name: "sysm"
};
</script>

<style>
/* CSS */
#app {
  border-radius: 50%;
  border: 1px solid white;
  margin: 4px;
  height: calc(100vh - 8px);
  width: calc(100vw - 8px);
  box-sizing: border-box;
}
:root {
  background: transparent;
}
body {
  margin: 0px;
  padding: 0px;
}
</style>
