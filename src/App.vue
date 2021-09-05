<template>
  <SelectColours class="component" id="colourSelector" v-show="showColourSelector" @submit-colours="submittedColours"/>
  <Animation v-bind:theme = "theme" class="component" v-show="showAnimation"/>
  <div class="background">
    <div class = "triangle" id = "topLeft"></div>
    <div class = "triangle" id = "topRight"></div>
    <div class = "triangle" id = "bottomLeft"></div>
    <div class = "triangle" id = "bottomRight"></div>
    <div class = "triangle" id = "bottomMiddle"></div>
    <img src="./assets/colourPalette.png" @click="handleChangeColour" v-if="showAnimation" id="changeColour">
  </div>

</template>

<script>
import SelectColours from './components/SelectColours.vue'
import Animation from './components/Animation.vue'
export default {
  name: 'App',
  components: {
    SelectColours,
    Animation
  },
   data () {
        return {
            showColourSelector: true,
            showAnimation: false,
            theme: null,
            background: null
        }
  },
  methods: {
    submittedColours({theme, background}) {
      this.showColourSelector =  false
      this.theme = theme
      this.background = background
      var backdrop = document.getElementsByClassName("background")
      for (var i = 0; i < backdrop.length; i++) {
          backdrop[i].style.backgroundColor = this.background
      }
      /*
      var elements = document.getElementsByClassName("animation")
      for (var i = 0; i < elements.length; i++) {
        console.log(elements[i])
      }
      
  */
      const gif = document.getElementById("gif")
      const finalImg = document.getElementById("finalImg")
      const rotateString = "hue-rotate(" + this.theme + "deg)";
      gif.style.filter = rotateString
      finalImg.style.filter = rotateString
      this.showAnimation = true;
    },
    handleChangeColour(e) {
      this.showColourSelector = true
    }
  }
}
</script>

<style>
  body {
    margin: 0px;
    overflow: hidden;
  }
  .background {
    width: 100vw;
    height: 100vh;
    padding: 0px;
    margin: 0px;
    background-color: rgb(255, 255, 255);
  }
  .triangle {
    width: 0;
    height: 0;
    position: absolute
  }
  #topLeft {
    border-right: 50vw solid transparent;
    border-bottom: 50px solid transparent;
    border-top: 50px solid rgba(0, 0, 0, 0.25);
    border-left: 50vw solid rgba(0, 0, 0, 0.25);
  }
  #topRight {
    margin-left: 43vw;
    border-right: 30vw solid rgba(0, 0, 0, 0.25);
    border-bottom: 30px solid rgba(0, 0, 0, 0.25);
    border-top: 30px solid transparent;
    border-left: 30vw solid transparent;
  }
  #bottomLeft {
    bottom: 0px;
    border-right: 20vw solid transparent;
    border-bottom: 50px solid rgba(0, 0, 0, 0.25);
    border-top: 50px solid transparent;
    border-left: 20vw solid rgba(0, 0, 0, 0.25);
  }
  #bottomRight {
    bottom: 0px;
    margin-left: 40vw;
    border-right: 30vw solid rgba(0, 0, 0, 0.25);
    border-bottom: 50px solid rgba(0, 0, 0, 0.25);
    border-top: 50px solid transparent;
    border-left: 30vw solid transparent;
  }
  #bottomMiddle {
    bottom: 4px;
    border-radius: 5%;
    margin-left: 16vw;
    border-right: 35vw solid transparent;
    border-bottom: 0px solid transparent;
    border-top: 60px solid rgba(0, 0, 0, 0.15);
    border-left: 24vw solid transparent;
  }
  .component {
    position: absolute;
  }
  #colourSelector {
    z-index: 100;
  }
  #changeColour {
    position: absolute;
    width: 75px;
    margin-left: 20px;
    margin-top: 10px;
  }
</style>
