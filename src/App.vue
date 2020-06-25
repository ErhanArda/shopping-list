<template>
  <div id="app">
  <h1>The Cup Store</h1>
            
        <product v-for="(product,id) in products" :key="id" :product="product"></product>

            <Product/>
            <Card/>  
            <!-- <Todo/> -->
            <div id="app" class="bg-gray-300 flex flex-col justify-center items-center h-20" >
            <InputField default="My default text" @dirty-field="dirty = $event"/>
            <p v-if="dirty" >Field is dirty</p>
        </div>
  </div>
</template>

<script>
import Card from './components/Card.vue'
import Product from './components/Product.vue'
// import Todo from './components/Todo'
import InputField from './components/InputField'


export default {
  name: 'App',
  created() {
        console.log('Vue instance created!')
  },
  mounted() {
    console.log('Vue instance mounted!')
    // fetch('https://jsonplaceholder.typicode.com/todos')
    //   .then(response => response.json())
    //   .then(json => this.todos = json )
  },
  destroyed() {
        console.log('Vue instance destroyed!')

  },
  beforeCreate() {
        console.log('Vue instance beforeCreate!')
  },
  components: {
    Card,
    Product,
    // Todo
    InputField
  },
  data: ()=> {
    return {
        dirty:false,

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
