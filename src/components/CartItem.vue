<template>
  <div class="cart-item">
    <img :src="obj.imgSrc" class="pic"/>
    <div class="text">
        <h3>{{ obj.name }}</h3>
        <p>מחיר: {{ obj.price }}</p>
        <button @click="remove()">הסר מהעגלה</button>
    </div>
    
  </div>
</template>

<script>
export default {
    props:{obj: Object,
        index: Number
    },
    methods : {
        remove(index){
            this.$emit('remove-item' , this.index , this.obj);
        }
    }
}
</script>

<style>
.cart-item{
    width: 97%;
    height: fit-content;
    border-style: solid;
    border-color: black;
    border-width: 2px;
    text-align: right;
}

.pic{
    position: relative;
    top:50%;
    left:0;
    width: 40%;
    height: 20%;
}

.text{
    position:relative;
}
</style>