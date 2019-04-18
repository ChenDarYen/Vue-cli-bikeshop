<template>
<nav class="d-none d-lg-block bg-light sidebar">
    <div class="pl-3">
        <h6 class="sidebar-heading px-3 py-2 mt-4 mb-1 text-muted">
            <span>Admin</span>
        </h6>
        <ul class="nav flex-column mb-2">
            <li class="nav-item">
                <router-link class="nav-link" :class="{'active': $route.name == 'Order'}" href="#"
                to="/admin">
                    <span data-feather="file-text"></span>
                    Order
                </router-link>
            </li>
            <li class="nav-item">
                <router-link class="nav-link" :class="{'active': $route.name == 'Product'}" href="#"
                to="/admin/product">
                    <span data-feather="file-text"></span>
                    Product
                </router-link>
            </li>
            <li class="nav-item">
                <router-link class="nav-link" :class="{'active': $route.name == 'Coupon'}" href="#"
                to="/admin/coupon">
                    <span data-feather="file-text"></span>
                    Coupon
                </router-link>
            </li>
        </ul>
    </div>
</nav>
</template>

<style scoped>
.sidebar {
    width: 150px
}
</style>
