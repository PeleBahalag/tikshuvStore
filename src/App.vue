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
import CartItem from './components/CartItem.vue';
  export default{
    components : {ItemComp, CartItem},
    data(){
      return{
        items:[
          {name : "ירין בן מכחול" , imgSrc : yarinBm , price : "12 שעות שינה" , inStock : true},
          {name : "ירין שיט" , imgSrc : yarinS , price : "100 קידודים" , inStock : true} ,
          {name : "עמית מה שלמה" , imgSrc : amit , price : "100 מילים בדקה" , inStock : true} ,
          {name : "יניב הייזמן" , imgSrc : yaniv, price : 420 , inStock : true} ,
          {name : "איתי לוי (לא הזמר)" , imgSrc : itay , price : "250 ש''ח לכרטיס'" , inStock : true} ,
          {name : "עומר תודה לאל" , imgSrc : omer , price : 1000000 , inStock : true} ,
          {name : "Jewish boy" , imgSrc : roee , price : "31 גימלים" , inStock : true} ,
          {name : "צ שחף סמל מחשוב" , imgSrc : shahaf , price : 749999 , inStock : true} ,
          {name : "גל בן אבו" , price : 750000 , inStock : true  } ,
          {name : "דניאל מדריכה" , imgSrc : daniel , price : 666 , inStock : true} ,
          {name : "טל שיר" , imgSrc : tal , price : 2000 , inStock : true},
          
        ],
        userItems : [] , 
        totalPriceNum : 0,
        totalPriceString : "",
        cartOpen : false,
        showPay : false
      }
    },
    methods : {
      toggleCart(){
        if(this.cartOpen){
          this.cartOpen = false;
        }
        else{
          this.cartOpen = true;
        }
      },
      itemAdded(index){
        this.cartOpen = true;
        this.items[index].inStock = false;
        this.totalPrice += this.items[index].price;
        this.userItems.push(this.items[index]);
      },
      removeItem(index , obj){
        const indexOfBoy = this.items.indexOf(obj);
        if (indexOfBoy !== -1) {
          this.items[indexOfBoy].inStock = true;
        }
        this.userItems.splice(index, 1);
      },
      pay(){
        this.userItems = [];
        this.showPay = true;
        this.cartOpen = false;
        this.items.forEach((item , index) => item.inStock = true);
        this.totalPrice = 0;
      }

    }
  }
</script>

<template>
  <div id="app">
    <div class="banner">
      <img src="./assets/cart.png" class="cart" @click="toggleCart()"/>
      <h1>חנות בני התקשוב</h1>
    </div>
    <div class="container">
      <item-comp v-for="(item, index) in items" :key="index" :obj="item" :index="index" @item-added="itemAdded"></item-comp>
    </div>
    <div class="cart-menu" v-show="cartOpen">
      <h2 v-show="userItems.length === 0">עוד לא הוספתם כלום לעגלה</h2>
      <div v-show="userItems.length > 0">
        <p>ברוכים הבאים לעגלה</p>
        <cart-item v-for="(item , index) in userItems" :key="index" :obj="item" :index="index" @remove-item="removeItem"></cart-item>
        <p>סה"כ לתשלום: {{ totalPrice }} ש"ח</p>
        <button class="pay" @click="pay">לתשלום</button>
      </div>
    </div>
    <div v-show="showPay" class="paymentDone">
      <h1>תודה על קנייתכם!</h1>
      <button @click="showPay = false" class="pay">לקניה נוספת</button>
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
  cursor: pointer;
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
  margin-bottom: 100px;
}

.cart-menu{
  width:15%;
  height:50%;
  position:absolute;
  left:5.5vw;
  top:15.8vh;
  background-color: white;
  border-radius: 25px;
  border-color: darkcyan;
  border-width: 3px;
  border-style:solid ;
  z-index:12;
  display: flex;
  flex-flow: column nowrap;
  overflow: auto;
}

.pay{
  background-color: darkcyan;
  margin:3%;
}

.paymentDone{
  width:100%;
  height:100%;
  background-color: black;
  border-color: darkcyan;
  border-width: 3px;
  color:rgb(0, 0, 0) !important;
  z-index: 50;
  position: fixed;
  top:0;
  right:0;
  display: flex;
  flex-direction: column;
  justify-content: center;
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
  .cart-menu{
    left:20vw;
    width: 50%;
  }
}
</style>
