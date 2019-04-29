<template>
<div class="footer">
    <div class="row">
        <form class="form-inline d-flex flex-column col-12 col-lg-6">
            <div class="row">
                <input type="email" class="form-control ml-auto col-12 col-lg-7" placeholder="填入電子郵件接受促銷資訊">
                <button class="btn btn-danger mt-2 mt-lg-0 ml-lg-1 col-12 col-lg-3" type="submit">加入</button>
            </div>
        </form>
        <div class="icon mt-4 mt-lg-0 col-lg-6 text-center">
            <i class="fab fa-line"></i>
            <i class="fab fa-facebook"></i>
            <i class="fab fa-weixin"></i>
        </div>
    </div>
</div>
</template>
<script>
</script>
<style lang="scss" scoped>
@import "@/assets/all.scss";

.footer {
    width: 100vw;
    overflow: hidden;
    padding: 40px 30px 70px;
    background-color: $dark;
}
.form-inline .row {
    width: 100%
}
.icon {
    font-size: 30px;
    color: $light;
    .fab {
        margin: 0 15px
    }
}
.fa-facebook:hover {
    color: #3b5998;
}
.fa-line:hover {
    color: #00b900;
}
.fa-weixin:hover {
    color: #00d405;
}

</style>