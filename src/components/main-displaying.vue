<template>
<div class="container-fluid">
    <div class="row">
        <swiper :options="swiperOption">
            <swiper-slide v-for="(item, index) in swiperBanner" :key="index">
                <div class="banner">
                    <div class="background" :style="{'background-image': `url('${item.url}')`}"></div>
                    <div class="content text-white text-center">
                        <h3>{{ item.subtitle }}</h3>
                        <h2>{{ item.title }}</h2>
                        <router-link class="btn btn-dark mt-2" :to="item.path">{{ item.buttonText }}</router-link>
                    </div>
                </div>
            </swiper-slide>
            <div class="swiper-button-prev" slot="button-prev"></div>
            <div class="swiper-button-next" slot="button-next"></div>
            <div class="swiper-pagination" slot="pagination"></div>
        </swiper>
    </div>
    <div class="row">
        <div class="col-12 col-lg-6">
            <Window :options="touringOptions"/>
        </div>
        <div class="col-12 col-lg-6">
            <Window :options="pistaOptions"/>
        </div>
        <div class="col-12">
            <Window :options="salesOptions"/>
        </div>
    </div>
</div>
</template>

<script>
import Window from '@/components/window';

export default {
    data() {
        return {
            swiperBanner: [
                {
                    title: 'BIKE SHOP周年慶',
                    subtitle: 'life is keep riding.',
                    buttonText: '限時特惠',
                    url: 'https://images.unsplash.com/photo-1541625602330-2277a4c46182?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=750&q=80',
                    path: '/shop/sales'
                },
                {
                    title: '踏上屬於你的旅行',
                    subtitle: 'on the road.',
                    buttonText: '了解旅行車',
                    url: 'https://images.unsplash.com/photo-1485203665302-548a1845d137?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=747&q=80',
                    path: '/shop/touring'
                },
                {
                    title: '單速車系列',
                    subtitle: '城市騎行',
                    buttonText: '查看更多',
                    url: 'https://images.unsplash.com/photo-1452117774045-dfd7a5e9718c?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=889&q=80',
                    path: '/shop/pista'
                },
            ],
            swiperOption: {
                autoplay: true,
                speed: 3000,
                loop: true,
                autoplayDisableOnInteraction: false,
                navigation: {
                    nextEl: '.swiper-button-next',
                    prevEl: '.swiper-button-prev',
                },
                 pagination: {
                    el: '.swiper-pagination',
                    clickable :true
                },
            },
            touringOptions: {
                title: '旅行車',
                subtitle: 'Touring Bike',
                direction: '/shop/touring',
                styles: {
                    color: 'white',
                    backgroundImage: 'url("https://images.unsplash.com/photo-1511994298241-608e28f14fde?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=750&q=80")',
                }
            },
            pistaOptions: {
                title: '單速車',
                subtitle: 'Pista Bike',
                direction: '/shop/pista',
                styles: {
                    backgroundImage: 'url("https://images.unsplash.com/photo-1507035895480-2b3156c31fc8?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=750&q=80")',
                }
            },
            salesOptions: {
                title: '特價區',
                subtitle: 'Sales',
                direction: '/shop/sales',
                styles: {
                    backgroundImage: 'url("https://images.unsplash.com/photo-1544011343-494fe72e6bab?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=500&q=60")',
                    color: 'white',
                }
            },
        }
    },
    components: {
        Window,
    },
}
</script>

<style acoped>
</style>
