<template>
  <div id="app">
    <div class="topBar">
      <span><b>LEANAFY</b> / Warehouse Onboarding</span>
    </div>
    
    <router-view />
  </div>
</template>

<script>

</script>

<style>
body{
  margin: 0;
  padding: 0;
  background-color: rgb(247, 245, 255);
}
.topBar{
  height: 60px;
  padding: 0 50px;
  display: flex;
  align-items: center;
  /* position: fixed; */
  background-color: #fff;
  border-bottom: 1px rgb(238, 238, 238) solid;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}

</style>
