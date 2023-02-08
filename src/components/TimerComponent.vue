<template>
  <div>
    <h1 @click="operotor" @dblclick="resetTimer"  class="timer-display">{{ display }}</h1>
  </div>
</template>

<script>

export default {
    data(){
        return{
            display:"00 : 00 : 00",
            timeBegan:null,
            timeStopped:null,
            stoppedDuration:0,
            startInterval:null,
            flag:false,
        }
    },

    methods:{

        operotor(){
            if(!this.flag){
                this.startTimer();
                this.flag=true
            }
            else{
                this.stoppedTimer();
                this.flag=false
            }

        },

       startTimer(){
        console.log('start')
        if(this.timeBegan === null){
            this.timeBegan = new Date()
        }

        if(this.timeStopped !== null){
            this.stoppedDuration += (new Date() - this.timeStopped)
        }

        this.startInterval = setInterval(this.clockRunning, 10)
       },
       
       stoppedTimer(){
        this.timeStopped = new Date();
        clearInterval(this.startInterval)
       },

       clockRunning(){
        const currentTime = new Date();
        const timeElapsed = new Date(currentTime - this.timeBegan -this.stoppedDuration);

        let minutes = timeElapsed.getUTCMinutes();
        let seconds = timeElapsed.getUTCSeconds();
        let milliseconds = timeElapsed.getUTCMilliseconds();

        milliseconds = Math.floor(milliseconds / 10);

        this.display = (minutes= minutes < 10 ? '0' + minutes:minutes)+ ':' +
        (seconds = seconds < 10 ? '0' + seconds:seconds) + ":" +
        (milliseconds = milliseconds < 10 ? '0' + milliseconds:milliseconds);
       },

       resetTimer(){
        console.log('reset')
        clearInterval(this.startInterval);
        this.timeBegan = null;
        this.timeStopped = null;
        this.stoppedDuration = 0;
        this.display="00 : 00 : 00";
        this.flag = false;
       }
    }
}
</script>

<style scoped>
.timer-display{
min-width: 400px;
color: white;
text-align: center;
font-size: 100px;
margin: 0;
}
</style>