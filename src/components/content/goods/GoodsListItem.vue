<template>
    <div class="goods-item">
        <img :src="goodsItem.show.img" alt="">
        <div class="goods-info">
            <p>{{goodsItem.titles}}</p>
            <span class="price">{{goodsItem.price}}</span>
            <span class="collect">{{goodsItem.cfav}}</span>
        </div>
    </div>
</template>
<script>
export default {
    name:"GoodsListItem",
    props:{
        goodsItem:{
            type:Object,
            default(){
                return {}
            }
        }
    },
    methods: {
        itemImgLoad() {
            this.$bus.$emit('itemImgLoad');
        },
        itemLink() {
            this.$router.push('/detail/' + this.goodsItem.iid)
        }
    },
    computed: {
        showImg(){
            return this.goodsItem.image || this.goodsItem.show.img;
        }
    }
}
</script>
<style>
.good-item{
    padding-bottom: 40px;
    position: relative;
    width: 30%;
}
.good-item img{
    width: 100%;
    border-radius: 5px;
}
.good-info{
    font-size: 12px;
    position: absolute;
    bottom: 5px;
    left: 0;
    right: 0;
    overflow: hidden;
    text-align: center;
}
.good-info p{
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
    margin-bottom: 3px;
}
.good-info .price{
    color: var(--color-high-text);
    margin-right: 20px;
}
.good-info .collect{
    position: relative;    
}
.good-info .collect::before{
    content: '';
    position: absolute;
    left: -15px;
    top: -1px;
    width: 14px;
    height: 14px;
    background: url("~assets/images/home/collect_icon.png") 0 0/14px 14px;
}
</style>