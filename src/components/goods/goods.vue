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
    <div class="foods-wrapper"></div>
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
</style>
