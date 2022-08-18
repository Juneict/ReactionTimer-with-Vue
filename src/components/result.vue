<template>
     <p>Reaction Time : {{score}} s</p>
     <p class="rank">Rank {{rank}}</p>
</template>
<script>
    export default{
        props :['score'],
        data(){
            return{
                rank:null
            }
        },
        mounted(){
            if(this.score<2){
                this.rank = "goood"
            }else if(this.score<4){
                this.rank = "not bad"
            }else{
                this.rank = "stupid"
            }
        }
    }
   
</script>
<style>
.rank{
    font-size: large;
    font-weight: bold;
    color: rgb(44, 159, 121);
}
</style>