<script>
export default {
    data() {
        return {
            "products": []
        }
    },
    emits: ['add_product'],
    methods: {
        addToCart(product) {
            this.$emit('add_product', product)
        }
    },
    mounted() {
        fetch("https://fakestoreapi.com/products")
            .then(response =>
                response.json().then(
                    data => this.products = data
                ))
    }
}

</script>
<template>
    <main>
        <div id="products">
            <div class="cp-product" v-for="product in products" :key="product.id">
                <div class="cp-product-title">
                    <h3>{{ product.title }}</h3>
                </div>
                <div class="cp-product-image">
                    <img :src="product.image" alt="A product image" />
                </div>
                <div class="cp-product-description">
                    <p> {{ product.description }} </p>
                </div>
                <div class="cp-product-price">
                    <p>Price: {{ product.price }}</p>
                </div>
                <div class="cp-product-button">
                    <button @click="addToCart(product)"  class="cp-add-to-cart">Add to cart</button>
                </div>
            </div>
        </div>

    </main>
</template>
<style scoped>
#products {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr 1fr;
    gap: 1rem;
    padding: 0.75rem;
}


.cp-add-to-cart {
    cursor: pointer;
    background-color: #499451;
    color: white;
    border: 0.0625rem solid transparent;
    padding: 0.5rem 1rem;
    transition: all 1s;
}

.cp-add-to-cart:hover {
    background-color: #00824C;
    border: 0.0625rem solid #499451;;
}

.cp-product {
    background-color: #efefef;
    border: 0.0625rem solid #D8BFD8;
    padding: 0.5rem;
    max-width: 25vw;
    min-width: 18rem;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    align-items: center;
    height: 100%;
}

.cp-product-image {
    padding: 0.75rem;
    background-color: #fff;
    border: 0.0625rem solid #ccc;
    display: flex;
    justify-content: center;
    align-self: center;
    flex-basis: 20rem;
    flex-shrink: 0;
    flex-grow: 0;
    height: 20rem;
    & img {
        display: block;
        max-width: 20rem;
        max-height: 20rem;
    }
}

.cp-product-description {
    font-style: italic;
    font-size: 0.85rem;
    letter-spacing: 0.1rem;
    flex-grow: 1;
}


</style>