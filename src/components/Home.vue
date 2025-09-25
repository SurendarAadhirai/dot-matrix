<template>
  <div class="home-container">
    <h1>Happy breathing...</h1>  
  </div>
  <button @click="onClickButton"> {{  currentButtonLabel }} </button>
  <div v-if="currentButtonState">
    <p> {{ state }}</p>

  </div>
</template>
<script>
export default {
  name: 'HelloWorld',
  components: {
  },
  props: {
    msg: String
  },
  data () {
    return {
      currentButtonState: false,
      state: "Breathe In",
      currentButtonLabel: "Start",
      execute: null,
      interval: 1000
    }
  },
  methods: {
    onClickButton () {
      if (this.currentButtonLabel === "Start") {
        this.currentButtonLabel = "Stop"
        this.currentButtonState = true
        this.startProcessing()
      } else {
        this.currentButtonLabel = "Start"
        this.currentButtonState = false
        this.stopProcessing()
      }
    },
    startProcessing () {
      var str = ['Hold', 'Breathe Out', 'Hold', 'Breate In']
      let i = 0;
      console.log(this.currentButtonState)
      this.execute = setInterval(() => {
        this.state = str[i++]
        if( i === 4) {
          i = 0
        }
        if (i % 2 === 0) {
          this.interval = 5000;
        } else {
          this.interval = 1000;
        }
      }, 5000)
    },
    stopProcessing () {
      if (this.execute) {
        clearInterval(this.execute)
      }
    }

  },
}
</script>
<style scoped>
.home-container {
  margin-top: 5
}
</style>
