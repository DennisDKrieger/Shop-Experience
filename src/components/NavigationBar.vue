<template>
  <nav><h1>My items</h1> <div id="cartbox" @click="showCart"> <div id="amount">{{shoppingCart.length}}</div><img id="cart" src="../assets/cart.png">
    </div> 
    <transition name="fade">
    <div id="showCartContent" v-if="cartContent">
      <h3>My shoppingcart items</h3>
      <p class="summary-item" v-for="(product, index) in shoppingCart" v-bind:key="index">
        - {{product.title}} <img class="trash" src="../assets/trash.png" @click="deleteProduct(index)">
      </p>

  </div>
    </transition>
  </nav>
</template>

<script>
export default {
props:['shoppingCart'],
data(){
  return{
cartContent: false
  }
},
methods:{
  showCart(){
this.cartContent = !this.cartContent
  },
  deleteProduct(product){
     this.$emit('removeFromCart', product)
  }
}
}
</script>

<style>
nav{
  position: fixed;
    display: flex;
    justify-content: space-between;
    align-items: center;
    background-color:white;
    width: calc(100% - 4em);
    padding:0 2em;
    height: 100px;
}

#cart, #cartbox{
  width: 50px;
  height: 50px;
}

#cartbox{
  position: relative;
}

.summary-item{
 display: flex; 
 align-items:center;
}

.trash{
  width: 20px;
  height: 20px;
}


#amount{
  position: absolute;
  top: 0;
  right: 0;
  width: 20px;
  height: 20px;
  background:RGB(226, 81, 57);
  color: white;
  padding: 5px;
  border-radius: 50%;
}

#showCartContent{
  position: absolute;
  right: 0;
  top: 100px;
  width: 40vw;
  min-height: 100px;
  background-color: aliceblue;
  text-align: left;
  padding: 20px;
}

#showCartContent div{
  position: relative;
}


/* Transition */
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
} 




</style>