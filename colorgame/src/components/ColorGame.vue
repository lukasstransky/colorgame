<template>
  <div class="hello">
    <p style="font-size: 20vh" v-bind:style="{color: colors[textColorIndex]}">{{farben[colorIndex]}}</p>
    <p style="font-size: 5vh; margin-top: -15vh">Punkte: {{score}}</p>
    <p style="font-size: 3vh">Noch {{time}} Sekunden übrig</p>
  </div>
</template>

<script>
export default {
  name: 'ColorGame',
  data:() => ({
    colors: ["blue","red","green","purple","yellow"],
    farben: ["blau", "rot", "grün", "lila", "gelb"],
    keys: ["up","down","left","right","space"],
    score: 0,
    colorIndex: 0,
    textColorIndex: 0,
    time: 10,
    timer: {}
  }),
  methods:{
      getWord(){
        this.colorIndex = Math.floor(Math.random()*this.colors.length)
        this.textColorIndex = Math.floor(Math.random()*this.colors.length)
      },
      checkInput(keyCode){
        if(keyCode == 38 && this.textColorIndex == 0){ //arrow up & blau
            this.score++;
        }else if(keyCode == 40 && this.textColorIndex == 1){ //down & red
            this.score++;
        }else if(keyCode == 37 && this.textColorIndex == 2){ //left & green
            this.score++;
        }else if(keyCode == 39 && this.textColorIndex == 3){ //right & purple
            this.score++;
        }else if(keyCode == 32 && this.textColorIndex == 4){ //space & yellow
            this.score++;
        }else{
            this.score--;
        }
      },
      start () {
        this.timer = setInterval( () => {
            if (this.time > 0) {
                this.time--
            } else {
                clearInterval(this.timer)
                this.$emit("gameFinished", this.score)
            }
        }, 1000 )
    },
  },
  mounted(){
      let self = this
      this.start()
      this.getWord()
      window.addEventListener('keyup', function(ev){
        self.checkInput(ev.keyCode)
        self.getWord()
      })
  }
}
</script>

<style scoped>

</style>