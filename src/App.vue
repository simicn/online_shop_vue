<script>
import HeaderComponent from "./components/HeaderComponent.vue"
import NavigationComponent from "./components/NavigationComponent.vue"
import ProductsComponent from "./components/ProductComponent.vue"
export default {
  data() {
    return {
      
      'cart': new Map()
    
    }
  },
  components: {
    "header-component": HeaderComponent,
    "navigation-component": NavigationComponent,
    "products-component": ProductsComponent
  },
  methods:{
    addToCart(product){
      if(this.cart.has(product.id)){
        const p =this.cart.get(product.id)
        p.quantity++
        this.cart.set(p.id,p)
      }
      else{
        let item = product
        item.quantity = 1
        this.cart.set(product.id, item)
      }
      
    }
  }

}


</script>
<template>
  <header-component></header-component>
  <navigation-component :cart="cart"></navigation-component>
  <products-component @add_product="addToCart"></products-component>
</template>
<style scoped></style>