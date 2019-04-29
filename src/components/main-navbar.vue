<template>
<div>
    <nav class="navbar navbar-expand-sm navbar-light bg-light fixed-top flex-md-nowrap p-0">
        <router-link class="navbar-brand ml-3 px-2" to="/main">BIKE</router-link>
        <router-link class="ml-auto d-sm-none mr-2 mt-1" to="/cart"><Cart class="cart"/></router-link>
        <button class="navbar-toggler mx-2" type="button" data-toggle="collapse" data-target="#navbarCollapse">
            <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse pl-2" id="navbarCollapse">
            <ul class="navbar-nav mr-auto">
                <li class="nav-item">
                    <router-link class="nav-link" to="/">Home</router-link>
                </li>
                <li class="nav-item dropdown">
                    <router-link class="nav-link" to="/shop">商品</router-link>
                </li>
                <li class="nav-item">
                    <router-link class="nav-link" to="/shop/sales">特價區</router-link>
                </li>
            </ul>
            <form class="form-inline px-3 px-sm-0 row" @submit="search(keyWord)">
                <input class="form-control mr-2 col-8" type="search" placeholder="Search" aria-label="Search" v-model="keyWord">
                <button class="btn btn-outline-success my-2 my-sm-0 col-3" type="submit">Search</button>
            </form>
        </div>
        <router-link class="d-none d-sm-inline-block mr-4 ml-3 mt-1" to="/cart"><Cart class="cart"/></router-link>
        
    </nav>
</div>
</template>

<script>
import Cart from '@/components/cart';

export default {
    data() {
        return {
            keyWord: '',
        }
    },
    methods: {
        search(keyWord) {
            this.$router.push(`/shop/search/${keyWord}`)
        }
    },
    components: {
        Cart,
    }
}
</script>

<style scoped>
.navbar {
    height: 70px
}
.cart {
    margin: 8px 40px 0 20px;
}
#navbarCollapse {
    background-color: rgba(255, 255, 255, .7);
}
@media(min-width: 540px) {
    #navbarCollapse {
        background-color: inherit;
    }
}
</style>