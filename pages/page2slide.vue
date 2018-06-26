<template >
  <div class="box-all"  @mousedown="startDrag" @mousemove="doDrag">
    <div class="Screen" id="slide">
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
            <h1>SKYACTIVE-D</h1>
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
         document.getElementById("slide").style.transitionDuration = "0.5s";
         this.index=num;
      }
      else {
        document.getElementById("slide").style.transform = `translate(-${17*num}%)`;
         document.getElementById("slide").style.transitionDuration = "0.5s";
         this.index=num;
      }
    },
    startDrag(event) {
      this.x1 =event.clientX;
      this.y1 = event.clientY;
      this.dragging = true;
    },
    stop() {
      this.dragging = false;
      this.x2 = this.y2 = 0;
      this.x1 = this.y1 = 0;
      document.getElementById("slide").style.transform = `translate(-${17*this.index}%)`;
      document.getElementById("slide").style.transitionDuration = "0.5s";
    },
    doDrag(event) {
      if (this.dragging) {
        this.x2 = event.clientX;
        this.y2 = event.clientY;
        if(this.x2<this.x1){
          this.sumx = this.x1-this.x2;
          if(this.sumx>=50){
            if ( this.index <5 ){
                this.index++;
                this.dragging = false;
            }
          }
        }
        else {
          this.sumx = this.x2-this.x1;
          if (this.sumx>=50) {
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
    window.addEventListener('mouseup', this.stop);
  }

}
</script>

<style scoped>
  body {
    margin: 0;
  }
  h1 {
    font-size: 4rem;
  }
  .container{
    display: flex;
    height: 100%;
    width: 16%;
    min-height: 100vh;
    margin-left: 0.8%;
  }
  .box1{
    display: flex;
    flex-direction: column;
    height: 100%;
    min-height: 100vh;
    width: 75%;
  }
  .box{
    display: flex;
    flex-direction: column;
    height: 100%;
    min-height: 100vh;
    width: 100%;
  }
  .Screen {
    width: 400%;
    height: 100%;
    min-height: 100vh;
    display: flex;
    flex-direction: row;
    margin: 0 20%;
  }
  .box-all {
    height: 100%;
    width: 100%;
    overflow: hidden;
  }
  .content{
    display: flex;
    justify-content: center;
    align-items: flex-end;
    width: 100%;
    min-height: 15vh;
    padding-bottom: 1%;
   user-select: none;
  }
  .picture{
    width: 100%;
    height: 100%;
    min-height: 80vh;
   user-select: none;
  }
  img{
    width: 100%;
  }

</style>
