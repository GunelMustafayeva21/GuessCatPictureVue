<template>
    <div class="card">
        
        <img :src="card.image">
    </div>
</template>
<script>
export default{
    props:["card"]
}
</script>
<style scoped>
.card{
    width:200px;
    height:232px;
    border-radius: 10px;
    border: 3px solid whitesmoke;
    transition: box-shadow 0.4s;
    margin-left: 20px;
    
}
.card:hover{
    box-shadow: 0px 5px 40px rgb(202, 198, 198);
    transition: box-shadow 0.4s;
}
.card img{
    width:100%;
    height:100%;
}
</style>