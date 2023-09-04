<script>
import CartComponent from './CartComponent.vue';
export default {
    props: ["cart"],
    components: {
        "cart-component": CartComponent
    }
}
</script>
<template>
    <nav role="main" class="main-navigation">
        <ul>
            <li><a href="https://www.google.com/">Home</a></li>
            <li><a href="productd">Products</a></li>
            <li><a href="#">About us</a></li>
            <li><a href="#">Contact</a></li>
        </ul>
        <ul>
            <li><a href="#">Sign Up/Register</a></li>
            <cart-component :cart="cart"></cart-component>
                
           
            
        </ul>
    </nav>
</template>
<style scoped>
.main-navigation {
    background-color: #B02871;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0.5rem;
}

.main-navigation a {
    color: #fff;
    text-decoration: none;
}

.main-navigation a:hover {
    color: black;
}

.main-navigation > ul {
    list-style: none;
    margin: 0;
    padding: 0;
    display: flex;
    align-items: center;
}

.main-navigation > ul > li {
    margin: 0 0.5rem;
}
</style>