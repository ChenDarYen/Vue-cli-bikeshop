<template>
<div class="col">
    <div class="vld-parent">
        <Loading :active.sync="isLoading" ></Loading>
    </div>
    <div class="product-header row">
        <div class="text-center col-12 col-lg-4 ml-auto">
            <div class="product-title">{{ product.title }}</div>
            <div class="mb-4">
                <span class="product-originprice" 
                v-if="product.origin_price !=  product.price">{{ product.origin_price | currencyFilter }}</span>
                <span class="product-price">{{ product.price | currencyFilter }}</span>
            </div>
        </div>
        <div class="col-12 col-lg-7 mt-lg-4">
            <div class="row">
                <div class="form-group row"
                :class="{'col-7': !errors.has('quantity'), 'col-lg-3': !errors.has('quantity'),
                'col-8': errors.has('quantity'), 'col-lg-5': errors.has('quantity')}">
                    <label for="quantity" class="ml-auto text-right">數量：</label>
                    <select name="quantity" id="quantity" class="col-3 col-lg-6 px-2" 
                    v-model="form.qty" v-validate="'min_value:1'" :class="{'border-danger':errors.has('quantity')}">
                        <option v-for="num in Number(optionNum)" :value="num" :key="num">{{ num }}</option>
                    </select>
                    <span class="text-danger text-left px-1" v-if="errors.has('quantity')">請選擇數量</span>
                </div>
                <div class="text-left"
                :class="{'col-5': !errors.has('quantity'), 'col-4': errors.has('quantity'), 'pl-2': errors.has('quantity')}">
                    <button type="button" class="btn btn-outline-primary btn-sm"
                    @click="addToCart(product.id, form.qty)">
                            <i class="fas fa-spinner fa-spin" 
                            v-if="fileUpLoading"></i>
                            加到購物車
                    </button>
                </div>
            </div>
        </div>
    </div>
    <div class="row product-body">
        <span>{{ product.content }}</span>
    </div>
    <div class="row product-footer">
        <span>{{ product.description }}</span>
    </div>
</div>
</template>

<script>
export default {
    data() {
        return {
            productId: '',
            isLoading: false,
            fileUpLoading: false,
            product: {},
            bannerOptions: {},
            form: {
                product_id: '',
                qty: 0,
            },
            optionNum: 0,
        }
    },
    methods: {
        getProduct() {
            const vm= this;
            const api= `${process.env.APIPATH}/api/${process.env.CUSTOMPATH}/product/${vm.productId}`;
            vm.isLoading= true;
            this.$http.get(api).then((response) => {
                vm.product= response.data.product;
                vm.bannerOptions.imageUrl= response.data.product.imageUrl;
                vm.form.product_id= response.data.product.id;
                if(response.data.product.quantity > 10) {
                    vm.optionNum= 10
                }else {
                    vm.optionNum= response.data.product.quantity
                };
                vm.isLoading= false;
            })
        },
        addToCart(id, qty) {
            this.$validator.validate().then((result) => {
                if(result){
                    const vm= this;
                    const api= `${process.env.APIPATH}/api/${process.env.CUSTOMPATH}/cart`;
                    vm.fileUpLoading= true;
                    this.$http.post(api, {data: vm.form}).then((response) => {
                        vm.fileUpLoading= false;
                        if(response.data.success) {
                            this.$bus.$emit('message:push', `已成功將 ${vm.product.title} * ${vm.form.qty} 加入購物車`, 'success', '100%', '0');
                            this.$bus.$emit('cart:update');

                        }else {
                            this.$bus.$emit('message:push', `加入購物車失敗`, 'danger', '100%', '0');
                        }
                    })    
                }
            })
        },
        submitBannerOptions() {
            this.$emit('changeBanner', this.bannerOptions)
        },
    },
    created() {
        this.productId= this.$route.params.product_id;
        this.getProduct();
        this.submitBannerOptions();
    },
}
</script>

<style scoped>
.product-header label, span {
    line-height: 31px;
    margin-bottom: 0;
}
.product-header select, button {
    height: 31px;
}
.product-body {
    padding: 0 10%;
    font-size: 14px;
    line-height: 28px;
}
.product-footer {
    padding: 0 10%;
    font-size: 20px;
    line-height: 40px;
}
.product-title {
    font-weight: 900;
    font-size: 30px;
}
.product-originprice {
    text-decoration: line-through;
    font-size: 20px;
}
.product-price {
    font-size: 24px;
}
</style>