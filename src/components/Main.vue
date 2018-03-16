<template>
<section id="main" class="hero is-info is-fullheight is-bold">
  <div class="hero-body">
    <div class="container has-text-centered">

      <h2 class="title is-6">{{ this.message }}</h2>
  
      <!--  THE TIMER NUMBERS  -->
      <div id="timer">
        <span id="minutes">{{ minutes }}</span>
        <span id="middle">:</span>
        <span id="seconds">{{ this.getSeconds }}</span>
      </div>

      <!--  THE BUTTONS  -->
      <div id="buttons">
        
        <!--  START BUTTON    -->
        <button 
          @click="startTimer"
          v-show="!timerId"
          id="start"
          class="button is-dark is-large">
            <i class="fa fa-play-circle"></i>
        </button>
        
        <!--   PAUSE BUTTON   -->
        <button 
          @click="stopTimer"
          v-show="timerId"
          id="stop" 
          class="button is-dark is-large"> 
            <i class="fa fa-pause-circle"></i>
        </button>
        
        <!--  RESET BUTTON   -->
        <button
          @click="resetTimer"
          id="reset" 
          class="button is-dark is-large"> 
            <i class="fa fa-undo"></i>
        </button>
      </div>
  
    </div>
  </div>
</section>
</template>

<script>
export default {
  name: 'HelloWorld',
  data: function () {
    return {
      message: 'You loaded this page on ' + new Date().toLocaleString(),
      timerId: null,
      minutes: 25,
      seconds: 0
    }
  },
  computed: {
    // a computed getter
    getSeconds: function () {
      return (this.seconds >= 10) ? this.seconds : "0" + this.seconds
    }
  },
  methods: {
    startTimer () {
      this.timerId = setInterval(() => { 
        this.seconds--
        if (this.seconds < 0) {
          this.minutes--
          this.seconds = 59
        }
      }, 1000)
    },
    stopTimer () {
      clearInterval(this.timerId);
      this.timerId = null;
    },
    resetTimer () {
      this.minutes = 25
      this.seconds = 0
    }
  },
  created () {
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
#message {
  color: #DDD;
  font-size: 50px;
  margin-bottom: 20px;
}

#timer {
  font-size: 200px;
  line-height: 1;
  margin-bottom: 40px;
}
</style>
