<template >
  <div
    class="box"
    v-show="show2">
    <div class="header">
      <div class="headMes">
        <h2>Complete</h2>
      </div>
      <div class="exit">
        <button
          class="buttonCircle"
          @click="exit">X</button>
      </div>
    </div>
    <div class="content">
      <p>{{ numb }}</p>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    numb: {
      type: Number,
      required: true,
    },
    show2: {
      type: Boolean,
      required: true,
    },
  },
  data() {
    return {
    };
  },
  methods: {
    exit() {
      this.show2 = false;
    },
  },
};
</script>

<style scoped>
  .box {
    display: block;
    position: fixed;
    margin:10% 40%;
    width: 300px;
    height: 230px;
    border: 1px;
    /* background-color: green; */
  }
  .header {
    display: flex;
    width: 100%;
    height: 80px;
    border: 1px solid black;
    background-color: green;
  }
  .exit {
    width: 10%;
    height: 80px;
    display: flex;
    align-items: center;
    justify-content: center;

  }
  .headMes {
    text-align: center;
    width: 90%;
    height: 80px;
  }
  .buttonCircle {
    height: 30px;
    width: 30px;
    border-radius: 25px;
    color: black;
    font-weight: bold;
    border: 2px solid black;
  }
  .content {
    /* margin-left: 2px; */
    width: 100%;
    text-align: center;
    height: 150px;
    color: black;
    border:  1px solid black;
    /* background-color: blue; */
  }

</style>
