<template>
  <div class="selectColoursBackdrop">
      <div class="menu">
          <p class="menuText" id="topMenuText">Select Theme Colour</p>
          <div class="themeIcons">
              <img src="../assets/0icon.png" class="icon" id="360" @click="handleThemeColour">
              <img src="../assets/45icon.png" class="icon" id="45" @click="handleThemeColour">
              <img src="../assets/90icon.png" class="icon" id="90" @click="handleThemeColour">
              <img src="../assets/135icon.png" class="icon" id="135" @click="handleThemeColour">
              <img src="../assets/180icon.png" class="icon" id="180" @click="handleThemeColour">
              <img src="../assets/225icon.png" class="icon" id="225" @click="handleThemeColour">
              <img src="../assets/270icon.png" class="icon" id="270" @click="handleThemeColour">
              <img src="../assets/315icon.png" class="icon" id="315" @click="handleThemeColour">
          </div>
          <p class="menuText">Select Background Colour</p>
          <div class="backgroundIcons">
              <img src="../assets/ricon.png" class="icon" id="#ff7a63"  @click="handleBackgroundColour">
              <img src="../assets/oicon.png" class="icon" id="#ffa763" @click="handleBackgroundColour">
              <img src="../assets/yicon.png" class="icon" id="#ffe263" @click="handleBackgroundColour">
              <img src="../assets/gicon.png" class="icon" id="#acff63" @click="handleBackgroundColour">
              <img src="../assets/bicon.png" class="icon" id="#96b9ff" @click="handleBackgroundColour">
              <img src="../assets/picon.png" class="icon" id="#bc77fc" @click="handleBackgroundColour">
          </div>
          <p class="confirmButton" v-if="themeColour && backgroundColour" @click="$emit('submit-colours', {theme: themeColour, background: backgroundColour})">Confirm</p>
      </div>
  </div>
</template>

<script>
export default {
    name: 'SelectColours',
    data () {
        return {
            themeColour: null,
            backgroundColour: null
        }
    },
    methods: {
        handleThemeColour(event) {
            const selectedId = event.currentTarget.id
            var themes = document.getElementsByClassName("selectedTheme")
            for (var i = 0; i < themes.length; i++) {
                themes[i].classList.remove("selectedTheme")
            }
            var newTheme = document.getElementById(selectedId)
            newTheme.classList.add("selectedTheme")
            this.themeColour = parseInt(selectedId)

        },
        handleBackgroundColour(event) {
            const selectedId = event.currentTarget.id
            var backgrounds = document.getElementsByClassName("selectedBackground")
            for (var i = 0; i < backgrounds.length; i++) {
                backgrounds[i].classList.remove("selectedBackground")
            }
            var newBackground = document.getElementById(selectedId)
            newBackground.classList.add("selectedBackground")
            this.backgroundColour = selectedId
        },
    }

}
</script>

<style>
    .selectColoursBackdrop {
        top: 0;
        position: fixed;
        display: grid;
        background: rgba(0, 0, 0, 0.5);
        width: 100%;
        height: 100%;
    }
    .menu {
        height: 450px;
        width: 500px;
        background: white;
        justify-self: center;
        align-self: center;
        border-radius: 30px;  
        display: block; 
        

    }
    .themeIcons {
        margin-left: 50px;
        display: flex;
        justify-self: center;
        justify-content: center;
        flex-wrap: wrap;
        width: 400px;

    }
    .backgroundIcons {
        margin-left: 25px;
        display: flex;
        justify-self: center;
        justify-content: center;
        flex-wrap: wrap;
        width: 450px;
 
    }
    .icon {
        margin: 3px;
        padding: 5px;
        height: 50px;
        border: 2px solid transparent;
    }
    .menuText {
        text-align: center;
        font-family: Verdana;
        font-size: 20px;

    }
    #topMenuText {
        margin-top: 30px;
    }
    .confirmButton {
        margin-top: 25px;
        margin-left: 190px;
        padding: 5px;
        margin-bottom: 30px;
        align-self: top;
        text-align: center;
        justify-self: center;
        font-family: Verdana;
        font-size: 20px;
        border: 1px solid black;
        width: 120px;
        border-radius: 50px;
    }
    .confirmButton:hover {
        color: white;
        background: grey;
    }
    .selectedTheme {
        border: 2px solid black;
        border-radius: 100%;
    }
    .selectedBackground {
        border: 2px solid black;
        border-radius: 100%;
    }
</style>