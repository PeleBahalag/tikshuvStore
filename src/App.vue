<script>
import ItemComp from './components/ItemComp.vue';
import yarinBm from './assets/banim/yarinbm.jpg';
import yarinS from './assets/banim/yarins.jpg';
import amit from './assets/banim/amit.jpg';
import yaniv from './assets/banim/yaniv.jpg';
import itay from './assets/banim/itay.jpg';
import omer from './assets/banim/omer.jpg';
import roee from './assets/banim/roee.jpg';
import shahaf from './assets/banim/shahaf.jpg';
import daniel from './assets/banim/daniel.jpg';
import tal from './assets/banim/tal.jpg';
  export default{
    components : {ItemComp},
    data(){
      return{
        items:[
          {name : "ירין בן מכחול" , imgSrc : yarinBm , price : 0},
          {name : "ירין שיט" , imgSrc : yarinS , price : 0} ,
          {name : "עמית רומם" , imgSrc : amit , price : 0} ,
          {name : "יניב הייזמן" , imgSrc : yaniv, price : 0} ,
          {name : "איתי לוי (לא הזמר)" , imgSrc : itay , price : 0} ,
          {name : "עומר תודה לאל" , imgSrc : omer , price : 0} ,
          {name : "Jewish boy" , imgSrc : roee , price : 0} ,
          {name : "צ שחף סמל מחשוב" , imgSrc : shahaf , price : 0} ,
          {name : "דניאל מדריכה" , imgSrc : daniel , price : 0} ,
          { name : "טל שיר" , imgSrc : tal , price : 0}
        ]
      }
    }
  }
</script>

<template>
  <div id="app">
    <div class="banner">
      <img src="./assets/cart.png" class="cart"/>
      <h1>חנות בני התקשוב</h1>
    </div>
    <div class="container">
      <item-comp v-for="(item, index) in items" :key="index" :obj="item"></item-comp>
    </div>
  </div>
</template>

<style scoped>
#app{
  width:100vw;
  height: 100vh;
  position:absolute;
  top:0;
  right:0%;
}
.banner{
  width: 100vw;
  height: 14%;
  background-color: darkcyan;
  position:absolute;
  top:0;
  right:0%;
  display:flex;
  flex-flow: row nowrap;
  justify-content: space-between;
  align-items: center;
  padding-right:1% ;
}

.cart{
  height: 80%;
  width: 5%;
  padding-left: 2%;
}

h1{
  color:white;
}

.container{
  position: absolute;
  top:14%;
  width:90%;
  height:80%;
  right:0;
  display: flex;
  flex-flow: row wrap;
  overflow: auto;
}

@media (max-width: 480px) and (orientation: portrait){
  .cart{
    height: 40%;
    width: 13%;
  }
  h1{
    font-size: 2rem;
  }
  .container{
    right:0;
    top:14.3%;
    width: 87%;
  }
}
</style>
