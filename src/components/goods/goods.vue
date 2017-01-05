<template>
    <div class="goods">
    <div class="menu-wrapper">
        <ul>
            <li v-for="item in goods" class="menu-item">
                <span class="texts">
                    <span v-show="item.type>0" class="icon" :class="classMap[item.type]"></span>{{ item.name }}
                 </span>
            </li>
        </ul>
    </div>
    <div class="foods-wrapper">
        <ul>
            <li v-for="item in goods" class="food-list">
                <h1 class="titles">{{ item.name }}</h1>
                <ul>
                    <li v-for="food in item.foods" class="food-item">
                        <div class="icons">
                            <img :src="food.icon" width="57" height="57" >
                        </div>
                        <div class="contents">
                            <h2 class="names">{{ food.name }}</h2>
                            <p class="desc">{{ food.description }}</p>
                            <div class="extra">
                                <span class="count">月售{{ food.sellCount }}份</span>
                                <span>好评率{{ food.rating }}%</span>
                            </div>
                            <div class="price">
                                <span class="now">￥{{ food.price }}</span>
                                <span v-show="food.oldPrice" class="old">{{ food.oldPrice }}</span>
                            </div>
                        </div>
                    </li>
                </ul>
            </li>
        </ul>
    </div>
    </div>
</template>

<script>

    const ERR_OK = 0;

    export default{
        props: {
            seller: {
                type: Object
            }
        },
        data() {
          return {
            goods: []
          }
        },
        created() {
            this.classMap = ['decrease','discount','special','invoice','guarantee'];

            this.$http.get('/api/goods').then((response) => {
                response = response.body;
                if (response.errno === ERR_OK) {
                    this.goods = response.data;
                    console.log(this.goods);
                }
            });
        }
    };
</script>

<style>
    .goods{
        display: flex;
        position: absolute;
        width: 100%;
        top: 174px;
        bottom: 46px;
        overflow: hidden;
    }
    .menu-wrapper{
        flex: 0 0 80px;
        width: 80px;
        background: #f3f5f7;
    }
    .foods-wrapper{
        flex: 1px;
    }
    .menu-item{
        display: table;
        height: 54px;
        width: 56px;
        padding: 0 12px;
        line-height: 14px;
    }
    .icon{
        display: inline-block;
        vertical-align: top;
        width: 12px;
        height: 12px;
        margin-right: 4px;
        background-size: 12px 12px;
        background-repeat: no-repeat;
        background-image: url("decrease_1@2x.png");
    }
    .texts{
        display: table-cell;
        width: 56px;
        font-size: 12px;
        vertical-align: middle;
        border-bottom-style: solid;
        border-bottom-width: 1px;
        border-bottom-color: gainsboro;
    }
    .foods-wrapper{
        flex: 1px;
    }
    .titles{
        padding-left: 14px;
        height: 26px;
        lien-height: 26px;
        border-left: 2px solid #d99de1;
        font-size: 12px;
        color: rgb(147,153,159);
        background: #f3f5f7;
    }
    .food-item{
        display: flex;
        margin: 18px;
        padding-bottom: 18px;
        border-bottom-style: solid;
        border-bottom-width: 1px;
        border-bottom-color: gainsboro;
    }
    .food-item:nth-child{
        border: none;
        margin-bottom: 0px;
    }
    .icons{
        flex: 0 0 57px;
        margin-right: 10px;
    }
    .contents{
        flex: 1px;
    }
    .names{
        margin: 2px 0 8px ;
        height: 14px;
        line-height: 14px;
        font-size: 14px;
        color: rgb(7,17,27);
    }
    .desc, .extra{
        line-height: 10px;
        font-size: 10px;
        color: rgb(147,153,159);
    }
    .desc{
        line-height: 12px;
        margin-bottom: 8px;
    }
    .extra{

    }
    .count{
        margin-right: 12px;
    }
    .price{
        font-weight: 700;
        line-height: 24px;
    }
    .now{
        margin-right: 8px;
        font-size: 14px;
        color: rgb(240,20,20);
    }
    .old{
        text-decoration: line-through;
        font-size: 10px;
        color: rgb(147,153,159);
    }
    .cartcontrol-wrapper{
        position: absolute;
        right: 0;
        bottom: 12px;
    }

</style>
