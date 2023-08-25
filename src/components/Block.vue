<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
    <h2> Click Me</h2>
  </div>
</template>

<script>
export default {

    props : ['delay'],

    data() {
        return {
            showBlock : false,
            timer : null,
            reactionTimer : 0,
        }
    },

    mounted () {
        setTimeout(() => {
            this.showBlock = true
            console.log(this.delay)
            this.startTimer()
        } , this.delay)
    },

    methods : {
        startTimer (){

            this.timer = setInterval(() => {
                this.reactionTimer += 10
            } ,10)
        },

        stopTimer (){
            clearInterval(this.timer)
            this.$emit('end' , this.reactionTimer)
        }
    }

}
</script>

<style>

.block{
  width: 400px;
  border-radius: 20px;
  background: #0faf87;
  color: white;
  text-align: center;
  padding: 100px 0px;
  margin: 40px auto;
}

</style>