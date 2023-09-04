<script>
import CartItemComponent from './CartItemComponent.vue'
export default {
    data() {
        return { "dropdown": false }
    },
    props: ["cart"],
    components: {
        "cart-item": CartItemComponent
    },
    computed: {
        item() {
            return this.cart.value
        },
        total_items() {
            let total = 0
            for (let item of this.cart.values()) {
                total += item.quantity
            }
            return total
        },
        total_cost() {
            let total = 0
            for (let item of this.cart.values()) {
                total += item.quantity * item.price
            }
            return total
        },

    },
    methods: {
        toggleCartList() {
            this.dropdown = !this.dropdown
        }
    }
}
</script>
<template>
    <li id="cart" class="cp-cart-dropdown">
        <button @click="toggleCartList()" class="cp-cart-toggle">Cart (<span class="cp-item-count">{{total_items }}</span>)</button>
        <div class="cp-cart-items" :style="{ 'display': dropdown ? 'block' : 'none' }">
            <ul class="cp-item-list">
                <cart-item v-for="item in items" :key="item.id" :item="item">
                </cart-item>
            </ul>

            <p>Total cost <b class="cp-total-cost">{{ total_cost }}</b></p>
            <p><button class="cp-checkout-button">
                    Proceed to checkout
                </button></p>
        </div>
    </li>
</template>


<style scoped>
.cp-cart-dropdown {
    position: relative;
    display: inline-block;
}

.cp-cart-toggle {
    background-color: #B02871;
    color: white;
    padding: 10px;
    border: 1px solid #B02871;
    cursor: pointer;
}

.cp-cart-items {
    position: absolute;
    top: 100%;
    right: 0;
    width: 50vw;
    max-width: 30rem;
    min-width: 15rem;
    height: 30vh;
    max-height: 30rem;
    min-height: 15rem;
    overflow-y: scroll;
    background-color: #fff;
    border: 1px solid #000;
    padding: 10px;
    display: none;
}

.cp-cart-items ul {
    list-style: none;
    padding: 0;
    margin: 0;
    display: flex;
    flex-direction: column;
}

.cp-cart-items li {
    display: grid;
    grid-template-columns: 4.25rem 1fr 8rem 5rem;
    align-items: center;
    justify-content: space-between;
    margin-bottom: 10px;
}
</style>