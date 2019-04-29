<template>
<div>
  <Navbar :cart="cart"/>
  <Alert/>
  <router-view class="main"></router-view>
  <Footer class="mt-4"/>
</div>
</template>

<script>
import Navbar from '@/components/main-navbar';
import Footer from '@/components/main-footer';
import Alert from '@/components/alert';

export default {
  name: "adminPage",
  data() {
    return {
      cart: {},
      cartLen: 0,
    }
  },
  methods: {
    getCart() {
        const vm= this;
        const api= `${process.env.APIPATH}/api/${process.env.CUSTOMPATH}/cart`;
        this.$http.get(api).then((response) => {
          vm.cart= response.data.data;
          vm.cartLen= vm.cart.carts.length;
        })
    },
  },
  components: {
    Navbar,
    Footer,
    Alert,
  },
}
</script>