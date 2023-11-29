<template>
    <div>
        <h1>Shopping Cart</h1>
        <ul>
            <li v-for="(product, id) in products" :key="id">
                {{ product.title }} - {{ product.price | currency }} - {{ product.quantity }}
            </li>
        </ul>
        <p>Total: {{ total  | currency }}</p>
        <button @click="checkOut">Checkout</button>
        <p v-if="checkoutStatus">{{ checkoutStatus }}</p>
    </div>
</template>

<script>
import { mapState, mapGetters, mapActions } from 'vuex'
export default {
    computed: {
        ...mapGetters({
            products: 'cartProducts',
            total: 'cartTotal'
        }),
        ...mapState({
            checkoutStatus: 'checkoutStatus'
        }),
        // products(){
        //     return this.$store.getters.availableProducts
        // },
        // total(){
        //     return this.$store.getters.cartTotal
        // }

    },
    methods:{
        ...mapActions(['checkOut'])
    }

}
</script>

<style>

</style>