<script>
export default {
    props: ["item"]
}

</script>
<template>
    <div class="cp-cart-thumbnail">
        <img :src="item.image" />
    </div>
    <div class="cart-item-title">{{ item.title }}</div>
    <div class="cp-cart-item-quantity">
        <button class="cp-increase">+</button>
        <input class="cp-quantity" type="number" value="{{item.quantity}}" />
        <button class="cp-decrease">-</button>
    </div>
    <div class="cart-item-price">{{ item.price}}</div>
</template>
<style scoped>
.cp-cart-item-quantity {
    width: 8rem;
}

.cp-quantity {
    width: 3rem;
}

img {
    width: 3.25rem;
    height: 3.25rem;
    object-fit: cover;
}

h5 {
    margin: 0;
    font-size: 16px;
    font-weight: bold;
}

p {
    margin: 0;
    font-size: 14px;
}
</style>
