<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
    Click Me
  </div>
</template>

<script>
import { onUpdated } from '@vue/runtime-core'
export default {
    props:[
        'delay',
    ],data(){
        return{
            showBlock:false,
            timer:null,
            reactionTime:0,
        }
    },
    mounted(){
      setTimeout(()=>{
        this.showBlock=true
        this.startTimer()
      },this.delay)  
    },
    methods:{
        startTimer(){
            this.timer=setInterval(()=>{
                this.reactionTime+=10
            },10)
        },
        stopTimer(){
            clearInterval(this.timer)
            this.$emit('end',this.reactionTime);
        }
    }
}
</script>

<style scoped>
    .block{
        width:500px;
        background-color:rgb(194, 255, 235);
        color:rgb(42, 213, 213);
        border-radius:10px;
        padding:100px;
    }
</style>