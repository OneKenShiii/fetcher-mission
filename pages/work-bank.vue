<template lang="html">
  <div class="container" @mousedown="start" @mousemove="move">
    <div id="slide" class="body">
      <div @click="tran1()" class="content">
        <div class="header">
          <p>Driving Position</p>
        </div>
        <div class="pic">
          <img src="https://files.slack.com/files-pri/T2HCS6UT1-FBCFMPU9E/1.png" draggable="false">
        </div>
      </div>
      <div @click="tranx(1)" class="content">
        <div class="header">
          <p>G-Vectoring Control</p>
        </div>
        <div class="pic">
          <img src="https://files.slack.com/files-pri/T2HCS6UT1-FBD00NWQL/2.png" draggable="false">
        </div>
      </div>
      <div @click="tranx(2)" class="content">
        <div class="header">
          <p>SKYACTIVE DRIVE</p>
        </div>
        <div class="pic">
          <img src="https://files.slack.com/files-pri/T2HCS6UT1-FBD6LJLJE/3.png" draggable="false">
        </div>
      </div>
      <div @click="tranx(3)" class="content">
        <div class="header">
          <p>SKYACTIVE BODY & CHASSIS</p>
        </div>
        <div class="pic">
          <img src="https://files.slack.com/files-pri/T2HCS6UT1-FBD6LK15Y/4.png" draggable="false">
        </div>
      </div>
      <div @click="tranx(4)" class="content">
        <div class="header">
          <p>SKYACTIVE-D</p>
        </div>
        <div class="pic">
          <img src="https://files.slack.com/files-pri/T2HCS6UT1-FBD00Q63W/5.png" draggable="false">
        </div>
      </div>
      <div @click="tranx(5)" class="content">
        <div class="header">
          <p>SKYACTIVE-G</p>
        </div>
        <div class="pic">
          <img src="https://files.slack.com/files-pri/T2HCS6UT1-FBD6LKZM0/6.png" draggable="false">
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      x1: 0,
      y1: 0,
      x2: 0,
      y2: 0,
      sumx: 0,
      index: 0,
      dragging: false,
    };
  },
  methods: {
    tran1() {
        document.getElementById("slide").style.transform = "translateX(0)";
        document.getElementById("slide").style.transitionDuration = "0.5s";
        this.index = 0;
    },
    tranx(x) {
        document.getElementById("slide").style.transform = `translateX(-${32*x}%)`;
        document.getElementById("slide").style.transitionDuration = "0.5s";
        this.index = x;
    },
    start(event) {
      this.x1 = event.clientX;
      this.y1 = event.clientY;
      this.dragging = true;
    },
    move(event) {
      if (this.dragging) {
        this.x2 = event.clientX;
        this.y2 = event.clientY;
        if (this.x2 < this.x1) {
          this.sumx = this.x1 - this.x2;
          if(this.sumx > 50) {
            if (this.index < 5) {
              this.index++;
              this.dragging = false;
            }
          }
        } else {
          this.sumx = this.x2 - this.x1;
          if (this.sumx > 50) {
            if (this.index > 0) {
              this.index--;
              this.dragging = false;
            }
          }
        }
      }
    },
    stop() {
      this.x1 = this.y1 = 0;
      this.x2 = this.y2 = 0;
      this.dragging = false;
      document.getElementById("slide").style.transform = `translateX(-${32*this.index}%)`;
      document.getElementById("slide").style.transitionDuration = "0.5s";
    },
  },
  mounted() {
    window.addEventListener('mouseup', this.stop);
  },
}
</script>

<style scoped>
  .container {
    width               : 100%;
    height              : 100%;
    overflow            : hidden;
    /* background-color    : skyblue; */
  }
  .body {
    width               : 200%;
    height              : 100%;
    min-height          : 100vh;
    display             : flex;
    flex-direction      : row;
    margin              : 0 20%;
  }
  .content {
    display             : flex;
    flex-direction      : column;
    width               : 32%;
    height              : 100%;
    -moz-user-select    : none;
    -webkit-user-drag   : none;
    -webkit-user-select : none;
    -ms-user-select     : none;
    margin              : 0 1%;
  }
  .header {
    display             : flex;
    align-items         : flex-end;
    justify-content     : center;
    width               : 100%;
    height              : 15%;
    min-height          : 15vh;
    font-size           : 2rem;
    padding             : 1%;
    /* background-color    : tomato; */
  }
  .pic {
    display             : flex;
    align-items         : flex-start;
    justify-content     : center;
    width               : 100%;
    height              : 85%;
    min-height          : 85vh;
    -moz-user-select    : none;
    -webkit-user-drag   : none;
    -webkit-user-select : none;
    -ms-user-select     : none;
    /* background-color    : yellow; */
  }
</style>
