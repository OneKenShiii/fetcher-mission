<template >
  <div class="container"
    @mousemove="doDrag">
      <div
        class="dragstartzone"
        @mousedown="startDrag"
      >
        <div id="1" class="box-pic" style="display:block" >
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
        <div id="5" class="box-pic">
          <img src="./pic/5.png" draggable="false" >
        </div>
        <div id="6" class="box-pic">
          <img src="./pic/6.png" draggable="false">
        </div>
        <div id="7" class="box-pic">
          <img src="./pic/7.png" draggable="false">
        </div>
        <div id="8" class="box-pic">
          <img src="./pic/8.png" draggable="false" >
        </div>
        <div id="9" class="box-pic">
          <img src="./pic/9.png" draggable="false">
        </div>
        <div id="10" class="box-pic">
          <img src="./pic/10.png" draggable="false">
        </div>
        <div id="11" class="box-pic">
          <img src="./pic/11.png" draggable="false" >
        </div>
        <div id="12" class="box-pic">
          <img src="./pic/12.png" draggable="false">
        </div>
        <div id="13" class="box-pic">
          <img src="./pic/13.png" draggable="false">
        </div>
        <div id="14" class="box-pic">
          <img src="./pic/14.png" draggable="false" >
        </div>
        <div id="15" class="box-pic">
          <img src="./pic/15.png" draggable="false">
        </div>
        <div id="16" class="box-pic">
          <img src="./pic/16.png" draggable="false">
        </div>
        <div id="17" class="box-pic">
          <img src="./pic/17.png" draggable="false" >
        </div>
        <div id="18" class="box-pic">
          <img src="./pic/18.png" draggable="false">
        </div>
        <div id="19" class="box-pic">
          <img src="./pic/19.png" draggable="false">
        </div>
      <!-- <div>X: {{ x1 }}, Y: {{ y1 }}</div>
      <div>X: {{ x2 }}, Y: {{ y2 }}</div>
      <div>index : {{ index }}</div>
      <div>maxx : {{ maxx }}</div> -->
    </div>
  <!-- </div> -->
</div>
</template>

<script>

export default {
    data() {
      return {
        dragging: false,
        index: 1,
        x1: 0,
        y1: 0,
        x2: 1,
        y2: 0,
        modx: 0,
        maxx: 0
      }
      },
    methods: {
      startDrag(event) {
        this.x1 =event.clientX;
        this.y1 = event.clientY;
        this.dragging = true;
      },
      stopDrag() {
        this.dragging = false;
        this.x2 = this.y2 = 0;
        this.x1 = this.y1 = this.maxx = 0;
      },
      doDrag(event) {
        if (this.dragging) {
          this.x2 = event.clientX;
          this.y2 = event.clientY;

          if(this.x2>this.x1){
            this.modx = this.x2-this.x1;
            if(this.modx%2==0){
              document.getElementById(this.index).style.display = "none";
              this.index = this.index+1;
              if (this.index == 20) {
                this.index=1;
              }
              document.getElementById(this.index).style.display = "block";
              this.x1 = this.x2;
            }
          }
          if(this.x2<this.x1){
            this.modx = this.x1-this.x2;
            if(this.modx%2==0){
              document.getElementById(this.index).style.display = "none";
              this.index = this.index-1;
              if (this.index == 0) {
                this.index=19;
              }
              document.getElementById(this.index).style.display = "block";
              this.x1 = this.x2;
            }
          }
        }
      },
    },
    mounted() {
      window.addEventListener('mouseup', this.stopDrag);
    }
};
</script>

<style >
  .container {
  height: 100%;
  min-height: 100vh;
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  }
  .dragstartzone {
    display: flex;
    justify-content: center;
    align-items: center;
    user-select: none; /* Standard syntax */
}
  .box-pic {
  display: none;
  }
</style>
