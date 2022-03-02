<template>
  <div class="grid">
<div class="grid-item"  v-for="item in items" v-bind:key="item.id">
    <div class="productimage" :style="'background-image: url(' + item.image + ')'"></div>
    <div class="content">
<h3>{{item.title.substring(0,20) +"..."}}</h3>
<p>{{item.description.substring(0,50)+"..."}}</p>
<button class="add" @click="onClick(item)" >Add to Cart</button>
    </div>
</div>


  </div>
</template>

<script>

export default {
   props: ['items'],
methods:{
    onClick (event){
       this.$emit('addToCart', event)
     
    }
}

   
}
</script>

<style>
.grid{
    margin-top:100px;
    display: flex;
    width: 100%;
    flex-wrap:wrap;
    background-color: rgb(204, 204, 204);
}

.grid-item{
    width: calc(33.3% - 40px);
    margin: 20px;
    padding: 20px;
    box-sizing: border-box;
    aspect-ratio: 1/1;
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    align-items: flex-end;
    background-color: white;
    border-radius: 5%;
}

.productimage{
    width: 100%;
    height: 60%;
    background-position: center center;
    background-size: contain;
    background-repeat: no-repeat;
}



button.add{
    margin: 10px 0 0 0;
    border: none;
    background-color: RGB(226, 81, 57);
    color: white;
    padding: 10px 20px;
    border-radius: 20px;
}
</style>