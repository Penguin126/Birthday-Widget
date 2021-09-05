<template>
  <div class="wrapper">
      <div class="playButton" v-if="!initialized" @click="startAnimation"></div>
      <img src = "../assets/happyBirthdayGif.gif" v-show="playing" id="gif">
      <img src = "../assets/happyBirthdayMessage.png" v-show="stopped" id="finalImg">
      <img src = "../assets/replay.png" v-show="replay" id="replayButton" @click="startAnimation">

  </div>
</template>

<script>
export default {
    name: 'Animation',
    props: ['theme'],
    data () {
        return {
            initialized: false,
            playing: false,
            stopped: false,
            replay: false
        }
    },
    methods: {
        startAnimation() {
            this.playing = true
            this.initialized = true
            this.stopped = false
            this.replay = false;
            setTimeout(() => {
                this.stopped = true;
                setTimeout(() => {
                    this.playing = false;
                    this.replay = true;
                }, 1000)
            }, 3620)
        },
    }
}
</script>

<style>
  .wrapper {
        top: 0;
        position: fixed;
        display: grid;
        width: 100%;
        height: 100%;
        justify-content: center;
        align-content: center;
    }
  .playButton {
      width: 150px;
      height: 150px;
      background: url("../assets/pb1.png");
      background-size: contain;
  }
  .playButton:hover {
       background: url("../assets/pb2.png");
      background-size: contain;
  }
  #finalImg {
      left: 50%;
      margin-left: -325px;
      top: 54%;
      margin-top: -325px;
      position: absolute;
      width: 650px
  }
  #replayButton {
      position: absolute;
      left: 50%;
      margin-left: -20px;
      top: 82%;
      width: 40px;
  }
  #replayButton:hover {

  }
</style>