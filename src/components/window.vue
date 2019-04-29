<template>
    <div class="showcase" :style="options.styles">
        <div class="content">
            <span>{{ options.subtitle }}</span>
            <h3 class="mt-1">{{ options.title }}</h3>
            <p class="mt-2">{{ options.content }}</p>
            <button type="button" class="btn btn-dark mt-2" @click="directTo(options.direction)">前往</button>
        </div>
    </div>
</template>

<script>

export default {
    props: {
        options: {
            title: '',
            subtitle: '',
            content: '',
            direction: '',
            styles: {
                height: '',
                width: '',
                color: '',
                backgroundImage: '',
            },
        }
    },
    methods: {
        directTo(path) {
            this.$router.push(path)
        },
    }
}
</script>

<style lang="scss" scoped>
.showcase {
    height: 350px;
    background-repeat: no-repeat;
    background-size: 100% auto;
    background-repeat: no-repeat;
    background-position: bottom center;
    margin: 5px;
    position: relative;
    text-align: center;
    display: block;
    overflow: hidden;
    div {
        display: inline-block;
        vertical-align: middle;
    }
}
.bgImg {
    width: 100%;
    filter: blur(1px);
    img {
    width: 100%;
    }
}
.content {
    height: 93px;
    margin: auto;
    position: absolute;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0
}
h3 {
    font-weight: 1000;
    font-size: 30px;
}
</style>