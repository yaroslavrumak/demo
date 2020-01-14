<template>
  <div id="app">
    <HelloWorld />
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";

export default {
  name: "app",
  components: {
    HelloWorld
  }
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css?family=Source+Code+Pro&display=swap");

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  overflow: hidden;
}
body {
  min-width: 100vw;
  min-height: 100vh;
  background: #ddeefc;
  display: flex;
}
p,
input,
select,
label {
  font-family: "Source Code Pro", monospace;
}
input,
select {
  width: 100%;
  height: 50px;
  border-radius: 5px;
  box-shadow: none;
  border: 1px solid #ced6e0;
  transition: all 0.3s ease-in-out;
  font-size: 18px;
  padding: 5px 15px;
  background: none;
  color: #1a3b5d;
  margin-bottom: 20px;
  &:hover {
    border-color: #3d9cff;
  }
  &:focus {
    box-shadow: 0px 10px 20px -13px rgba(32, 56, 117, 0.35);
  }
}
label {
  font-size: 14px;
  margin-bottom: 5px;
  font-weight: 500;
  color: #1a3b5d;
  width: 100%;
  display: block;
  user-select: none;
}
#app {
  margin: auto;
}
</style>
