<template>
  <div id="app">
  <h1>The Cup Store</h1>
            
        <product v-for="(product,id) in products" :key="id" :product="product"></product>

            <Product/>
            <Card/>  

  </div>
</template>

<script>
import Card from './components/Card.vue'
import Product from './components/Product.vue'


export default {
  name: 'App',
  components: {
    Card,
    Product
  },
  data: ()=> {
    return {
        products: [
          { id: 120, name: 'Colorful Cups1', price: 999, image: '../images/cups1.jpg'},
          { id: 150, name: 'Colorful Cups2', price: 555, image: '../images/cups2.png'},
          { id: 200, name: 'Colorful Cups3', price: 111, image: '../images/cups1.jpg'},

          
        ]
      };
  }
}
</script>

<style>
@import './styles.css'
</style>
