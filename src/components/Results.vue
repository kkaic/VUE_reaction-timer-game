<template>
  <p>你花了{{ score }} 秒反應</p>
  <p class="rank">{{rank}}</p>
</template>

<script>
export default {
    props:['score'],
    data(){
        return{
            rank: null
        }
    },
    mounted(){
        if(this.score <250) {
            this.rank = '您是忍者'
        } else if(this.score < 400) {
            this.rank = '你像極了一隻豹'
        } else{
            this.rank = '你不如一隻烏龜'
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