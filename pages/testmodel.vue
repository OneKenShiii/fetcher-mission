<template >
  <div class="container">
    <div class="box">
    <div id="1" class="box-pic" style="display:block" draggable="false">
      <img src="./pic/1.png" draggable="false" >
    </div>
    <div id="2" class="box-pic">
      <img src="./pic/2.png" draggable="false" >
    </div>
    <div id="3" class="box-pic">
      <img src="./pic/3.png" draggable="false">
    </div>
    <div id="4" class="box-pic">
      <img src="./pic/4.png" draggable="false">
    </div>
  </div>
  <div class="box-button">
    <div class="box-right">
      <button
        class="add"
        @click="addindex">Add Index</button>
    </div>
    <div >
      {{ index }}
    </div>
  </div>
</div>
</template>

<script>
import ShowPicture from '~/components/ShowPicture.vue'

export default {
  components: {
    ShowPicture,
  },
  data(){
    return {
      index: 1,
      path: '',
    };
  },
  methods: {
    addindex() {
      document.getElementById(this.index).style.display = "none";
      this.index = this.index+1;
      if (this.index == 5) {
        this.index=1;
      }
      document.getElementById(this.index).style.display = "block";
    },
  },
};
</script>

<style scoped>
  .container {
    height: 100%;
    min-height: 100vh;
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
  }
  .box {
    height: 400px;
    width: 600px;
    border: 3px solid black;
  }
  .box-button {
    display: flex;
    justify-content: flex-end;
    width: 300px;
    height: 100px;
    background-color: orange;
  }
  .box-right {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100px;
    width: 150px;
  }
  .add{
    height: 70px;
    width: 100px;
  }
  .box-pic {
    display: none;
  }
</style>
