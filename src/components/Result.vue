<template>
    <div >
        <h2> your score is {{ result }} ms</h2>
        <p class="rank" > {{ rank }}</p>
    </div>
</template>

<script>
export default {
    props : ['result'],
    data (){
        return{
            rank : null,
        }
    },
    
    mounted (){
        if (this.result < 900){

            this.rank = 'you are soo fast'

        }else if (this.result < 1500){

            this.rank = 'you are pretty fast'

        }else {

            this.rank = 'you are too slow'
        }
    }
}
</script>

<style>
.rank{
  font-size: 1.4em;
  color: #0faf87;
  font-weight: bold;
}
</style>