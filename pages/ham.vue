<template >
  <body class="center-center">
    <div class="square"></div>
</body>
</template>

<script>
export default {
  create(){
      var myElement = document.getElementById('myElement');
      // create a simple instance
      // by default, it only adds horizontal recognizers
      var mc = new Hammer(myElement);

      // listen to events...
      mc.on("panleft panright tap press", function(ev) {
      myElement.textContent = ev.type +" gesture detected.";
      });
  }

}
</script>

<style lang="css">
* {
  box-sizing: border-box;
}
html, body {
  height: 100%;
}
body {
  background-color: #000;
  margin: 0;
}
.center-center {
  display: flex;
  justify-content: center;
  align-items: center;
}
.square {
  width: 90px;
  height: 90px;
  background-color: #00B0FF;
  transition: transform 300ms ease-out;
}
.expand {
  transform: scale(2.5);
}
</style>
