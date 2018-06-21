<template>
  <div class="box">
    <Mouse :render="__render"/>
  </div>

</template>

<script>
import Mouse from "./Mouse.js";
export default {
  name: "app",
  components: {
    Mouse
  },
  methods: {
    __render({ x}) {
      return (
        <h1>{x}</h1>
      );
    }
  }
};
</script>
<style>
.box {
  margin: 0;
  height: 600px;
  width: 600px;
  background-color: tomato;
}
</style>
