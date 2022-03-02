<template>


<navigation-bar :shoppingCart="shoppingCart" @removeFromCart="removing" />
<product-grid :items="items" @addToCart="adding" />
</template>

<script>
import NavigationBar from './components/NavigationBar.vue'
import ProductGrid from './components/ProductGrid.vue'

export default {
  name: 'App',
  components: {
    NavigationBar,
    ProductGrid
  },
   data(){
        return{
            items:[],
            shoppingCart:[]
        }
    },
     methods:{

adding(event){
this.shoppingCart.push(event);
},
removing(event){
 this.shoppingCart.splice(event, 1);
     }},

mounted(){
   this.axios.get('https://fakestoreapi.com/products').then((response) => {
        this.items = response.data
      })
  }
}
</script>

<style>
*{
  margin: 0px;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  background-color: #f3f2f2;
  overflow-y: hidden;
  
}
</style>
