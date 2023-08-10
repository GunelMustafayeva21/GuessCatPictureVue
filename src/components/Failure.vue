<template>
<div class="wrapper">
<h1>That was not correct!</h1>
<button @click="newGame">New Game</button>
</div>
</template>
<script>
export default {
    methods:{
        newGame(){
           this.$emit("activeComponentEvent", "app-game-cards");
        }
    }
}
</script>
<style scoped>
.wrapper{
    width:100%;
    height:100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    background-color:#9B6A6C;
    position: absolute;
    top: 0px;
    left:0px;
    
}
.wrapper h1{
    color:#E2B4BD;
    font-size: 40px;
}
.wrapper button{
    width: 200px;
    height: 50px;
    border-radius: 10px;
    background-color: #E2B4BD ;
    border: 1px solid #9B6A6C;
    color:#9B6A6C;
    font-size: 20px;
    font-weight: bold;
    transition: all 0.4s ease;
}
.wrapper button:hover{
    background-color: #F1DAC4;
    transition: all 0.4s ease;
    cursor: pointer;
}
</style>
