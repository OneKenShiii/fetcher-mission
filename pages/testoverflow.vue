<template >
  <div class="box-all" id="slide" @mousedown="startDrag" @mousemove="doDrag">
    <div class="Screen">
      <div class="container">
        <div class="box">
          <div class="content">
            <h1>Driving Position</h1>
          </div>
          <div class="picture" @click="move(0)">
            <img src=".\pic\drive.png" alt="car" class="img1" draggable="false" >
          </div>
        </div>
      </div>
      <div class="container">
        <div class="box">
          <div class="content">
            <h1>G-Vectoring Control</h1>
          </div>
          <div class="picture" @click="move(1)">
            <img src=".\pic\Control.png" draggable="false">
          </div>
        </div>
      </div>
      <div class="container">
        <div class="box">
          <div class="content">
            <h1>SKYACTIVE DRIVE</h1>
          </div>
          <div class="picture" @click="move(2)">
            <img src=".\pic\Sky.png" alt="car" draggable="false">
          </div>
        </div>
      </div>
      <div class="container">
        <div class="box">
          <div class="content">
            <h1>SKYACTIVE BODY & CHASSIS</h1>
          </div>
          <div class="picture" @click="move(3)">
            <img src=".\pic\Spirit.png" alt="car" draggable="false">
          </div>
        </div>
      </div>
      <div class="container">
        <div class="box">
          <div class="content">
            <h1>SSKYACTIVE-D</h1>
          </div>
          <div class="picture" @click="move(4)">
            <img src=".\pic\Green.png" alt="car" draggable="false">
          </div>
        </div>
      </div>
      <div class="container">
        <div class="box">
          <div class="content">
            <h1>SKYACTIVE-G</h1>
          </div>
          <div class="picture" @click="move(5)">
            <img src=".\pic\fu.png" alt="car" class="img1" draggable="false">
          </div>
        </div>
      </div>
    </div>

  </div>

</template>

<script>
export default {
  data() {
    return {
      dragging: false,
      index: 0,
      x1: 0,
      y1: 0,
      x2: 1,
      y2: 0,
      sumx: 0,
    }
    },
  methods: {
    move(num){
      if (num===0) {
        document.getElementById("slide").style.transform = `translate(0)`;
         document.getElementById("slide").style.transitionDuration = "1s";
         this.index=num;
      }
      else {
        document.getElementById("slide").style.transform = `translate(-${14.6*num}%)`;
         document.getElementById("slide").style.transitionDuration = "1s";
         this.index=num;
      }
    },
    startDrag(event) {
      this.x1 =event.clientX;
      this.y1 = event.clientY;
      this.dragging = true;
    },
    stopDrag() {
      this.dragging = false;
      this.x2 = this.y2 = 0;
      this.x1 = this.y1 = 0;
      document.getElementById("slide").style.transform = `translate(-${14.6*this.index}%)`;
      document.getElementById("slide").style.transitionDuration = "1s";
    },
    doDrag(event) {
      if (this.dragging) {
        this.x2 = event.clientX;
        this.y2 = event.clientY;

        if(this.x2<this.x1){
          this.sumx = this.x1-this.x2;
          if(this.sumx>=200){
            if ( this.index <5 ){
                this.index++;
                this.dragging = false;
            }
          }
        }
        else if(this.x2>this.x1){
          this.sumx = this.x2-this.x1;
          if (this.sumx>=200) {
            if ( this.index >0 ) {
              this.index--;
              this.dragging = false;
            }
          }
        }
      }
    },
  },
  mounted() {
    window.addEventListener('mouseup', this.stopDrag);
  }

}
</script>

<style scoped>
  body{
    margin: 0;
  }
  .Screen {
    width: 200%;
    height: 100%;
    min-height: 100vh;
    display: flex;
    flex-direction: row;
    overflow: scroll;

  }
  .container{
    display: flex;
    height: 100%;
    width: 60%;
    min-height: 100vh;
    /* overflow: hidden; */
    /* background-color: black; */
    margin-left: 0.8%;
    /* justify-content: center; */
    /* position: fixed; */
    /* align-items: center; */
  }
  .box1{
    display: flex;
    flex-direction: column;
    height: 100%;
    min-height: 100vh;
    width: 75%;
    /* background-color: tomato; */
    /* position: fixed; */
  }
  .box{
    display: flex;
    flex-direction: column;
    height: 100%;
    min-height: 100vh;
    width: 100%;
    /* background-color: tomato; */
  }
  .box-all {
    height: 100%;
    width: 100%;
    /* min-height: 100vh; */
    /* display: flex;
    flex-direction: row; */
    /* overflow: scroll; */
  }
  .content{
    display: flex;
    justify-content: center;
    align-items: flex-end;
    width: 100%;
    /* height: 100%; */
    min-height: 15vh;
    /* background-color: blue; */
    -webkit-user-select: none;
   -khtml-user-select: none;
   -moz-user-select: none;
   -o-user-select: none;
   user-select: none;
  }
  .picture{
    width: 100%;
    height: 100%;
    min-height: 80vh;
    /* background-color: pink; */
    -webkit-user-select: none;
   -khtml-user-select: none;
   -moz-user-select: none;
   -o-user-select: none;
   user-select: none;
  }
  /* .picMargin{
    display: flex;
    justify-content: center;
  } */

  .container1{
    display: flex;
    height: 100%;
    width: 100%;
    min-height: 100vh;
    /* overflow: hidden; */
    /* background-color: black; */
    justify-content: flex-end;
    /* position: fixed; */
    /* align-items: center; */
  }
  .containerEnd{
    display: flex;
    height: 100%;
    width: 100%;
    min-height: 100vh;
    /* overflow: hidden; */
    /* background-color: black; */
    justify-content: flex-start;
    margin-left: 0.8%;
    /* position: fixed; */
    /* align-items: center; */
  }

  img{
    width: 100%;
  }

</style>
