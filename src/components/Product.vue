<template>
    <div class="product-wrapper">
        <div class="product-image">
            <img v-if="!product.image" :src="product.image"> 
            <img v-else src="../images/cups1.jpg">
            <div class="product-image">
                {{'image-link: '+ product.image}}
            </div>
        </div>
        <div class="product-name">{{ product.name }}</div>
        <div class="product-price">{{ priceFormatted }}</div>
        <div><button @click.prevent="addProduct">ADD</button></div>
    </div>
</template>

<script>
import EventBus from '../bus'

    export default  {
        props: {
            product:[]
        },
        mounted() {
            console.log('Component instance mounted!')
        },
        computed: {
            priceFormatted: function () {
                return '$' + this.product.price / 100;
            }
        },
        methods: {
            addProduct: function(){
                EventBus.$emit('add-product', this.product)
            }
        },
    }
</script>

<style scoped>
    .product-wrapper {
        display: flex;
        align-items: center;
        justify-content: space-between;
        width: 100%;
        padding-bottom: 15px;
        border-bottom: 1px solid #eee;
        margin-bottom: 15px;
    }
    .product-image,
    .product-name,
    .product-price {
        margin: 0 10px;
    }
    img {
        width: 100px;
        height: 100px;
        object-fit: cover;
        border-radius: 9999px;
        border: 3px solid #fff;
    }
    button {
        background-color: #222;
        color: #eee;
        padding: 5px 10px;
        border-radius: 15px;
        margin-right: 15px;
    }
</style>