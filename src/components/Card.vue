<template>
    <div>
        <div>
            <ul>
                <li v-for="(product,id) in products" :key="id" class="price-row">
                    <div>{{product.name}}</div>
                    <div class="quantity-row">
                        <div class="price-quantity">Qty: {{product.qty}}</div>
                        <div>{{formatMoney(product.price * product.qty)}}</div>
                    </div>
                </li>
            </ul>
        </div>
        
        <div class="price-row">
            <div class="price-label">Sub-total</div>
            <div class="price-wrapper">{{formatMoney(subTotal)}}</div>
        </div>
        <div class="price-row">
            <div class="price-label">Shipping</div>
            <div class="price-wrapper">{{formatMoney(shipping)}}</div>
        </div>
        <div class="price-row">
            <div class="price-label">Total</div>
            <div class="price-wrapper">{{formatMoney(subTotal + shipping)}}</div>
        </div>
        <button class="checkout-button">CHECKOUT</button>
    </div>
</template>

<script>
  import EventBus from '../bus'

  export default {

    data: function(){
          EventBus.$on('add-product' ,(product) => {
            this.addProduct(product)
          })

      return{
        products:[]
      }
    },
    methods:{
      addProduct: function (product) {
                let productIndex = this.products.findIndex(function (currentProduct) {
                    return currentProduct.id === product.id;
                });
                
                if (productIndex >= 0) {
                    this.products[productIndex].qty++;
                    console.log(this.products);
                    return;
                }
                
                this.products.push({
                    ...product,
                    qty: 1,
                });
                
                console.log(this.products);
            },
          formatMoney: function(cents){
            return '$' + cents / 100
          }
        },
          computed: {
            subTotal: function () {
                let subtotal = 0;
                
                this.products.forEach( (product) => {
                    subtotal += product.price * product.qty;
                });
                return subtotal
            },
            shipping: function(){
              let totalQantity = 0;

                this.products.forEach((product)=>{
                  totalQantity += product.qty;
                })

                return totalQantity * 399
            }
        }
    }

</script>

<style scoped>
    .quantity-row {
        display: flex;
    }
    .price-quantity {
        margin-right: 15px;
    }
    .checkout-button {
        width: 100%;
        text-align: center;
        padding: 10px 0;
        background: #000;
        color: #eee;
    }
    .price-row {
        display: flex;
        justify-content: space-between;
        border-bottom: 1px solid #eee;
        margin: 10px;
        padding-bottom: 10px;
    }
</style>