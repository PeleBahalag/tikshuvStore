<template>
    <div class="tikshuv-boy">
        <img class="picture" :src="obj.imgSrc"/>
        <h3>{{obj.name}}</h3>
        <p>מחיר: {{  obj.price }}</p>
        <button>הוסף לעגלה</button>
    </div>
</template>

<script>
export default{
    props:['obj']
}
</script>

<style scoped>
.tikshuv-boy{
    height:60%;
    width:23%;
    background-color: darkcyan;
    margin:3%;
    padding: 2%;
    color: white;
    border-radius: 25px;
}

.picture{
    height:50%;
    width:90%;
}

@media (max-width: 480px) and (orientation: portrait){
    .tikshuv-boy{
        width:40%;
        height:47%;
    }
    .picture{
        height:46%;
    }
}
</style>