<template>
    <div class="header">
        <div class="content-wrapper">
            <div class="avatar">
                <img  width="64" height="64" :src="seller.avatar">
            </div>
            <div class="content">
                <div class="title">
                    <span class="brand"></span>
                    <span class="name">{{ seller.name }}</span>
                </div>
                <div class="description">
                    {{ seller.description }}/{{ seller.deliveryTime }}分钟送达
                </div>
                <div v-if="seller.supports" class="support">
                    <span class="icon"></span>
                    <span class="text">{{ seller.supports[0].description }}</span>
                </div>
            </div>
            <div v-if="seller.supports" class="support-count" @click="showDetail">
                <span class="count" >{{ seller.supports.length }} 个</span>
                <i class="icon-keyboard_arrow_right">></i>
            </div>
        </div>
        <div class="bulletin-wrapper" @click="showDetail">
            <span class="bulletin-title"></span><span class="bulletin-text">{{ seller.bulletin }}</span>
            <i class="icon-keyboard_arrow_rights">></i>
        </div>
        <div class="background">
            <img :src="seller.avatar" width="100%" height="100%">
        </div>
        <div v-show="detailShow" class="detail">
            <div class="detail-wrapper clearfix">
                <div class="detail-main">
                    <h1 class="name">{{ seller.name }}</h1>
                </div>
            </div>
            <div class="detail-close">
                <i class="icon-close">X</i>
            </div>
        </div>
    </div>
</template>

<script>
    export default{
        props: {
          seller: {
            type: Object
          }
        },
        data(){
            return {
                detailShow: false
            };
        },
        methods: {
            showDetail() {
                this.detailShow = true;
            }
        }
    }
</script>

<style>
    .header{
        position: relative;
        color:#fff;
        background: rgba(7,17,27,0.5);
        overflow: hidden;
    }
    .background{
        position: absolute;
        top: 0px;
        left: 0px;
        width: 100%;
        height: 100%;
        z-index: -1;
        filter: blur(10px);
    }
    .content-wrapper{
        padding: 24px 12px 18px 24px;
        font-size: 0;
        position: relative;
    }
    .avatar{
        display: inline-block;
        vertical-align: top;
    }
    .avatar img{
        border-radius: 2px;
    }
    .content{
        display: inline-block;
        margin-left: 16px;
    }
    .support-count{
        position: absolute;
        right: 12px;
        bottom: 14px;
        padding: 0 8px;
        height: 24px;
        line-height: 24px;
        border-radius: 14px;
        background: rgba(0,0,0,0.2);
        text-align: center;
    }
    .count{
        font-size: 10px;
    }
    .icon-keyboard_arrow_right{
        lien-height: 24px;
        margin-left: 2px;
        font-size: 10px;
    }

    .title{
        margin: 2px 0 8px 0;
    }
    .brand{
        display: inline-block;
        vertical-align: top;
        width: 30px;
        height: 18px;
        background-image: url("brand@2x.png");
        background-size: 30px 18px;
        background-repeat: no-repeat;
    }
    .name{
        margin-left: 6px;
        font-size: 16px;
        line-height: 18px;
        font-weight: bold;
    }
    .description{
        margin-bottom: 10px;
        line-height: 12px;
        font-size: 12px;
    }
    .support{

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
    .text{
        line-height: 12px;
        font-size: 10px;
    }
    .bulletin-wrapper{
        position: relative;
        height: 28px;
        line-height: 28px;
        padding: 0 22px 0 12px;
        white-space: nowrap;
        overflow: hidden;
        text-overflow: ellipsis;
        background: rgba(7,17,27,0.2);
    }
    .bulletin-title{
        display: inline-block;
        vertical-align: top;
        margin-top: 8px;
        width: 22px;
        height: 12px;
        background-image: url("bulletin@2x.png");
        background-size: 22px 12px;
        background-repeat: no-repeat;
    }
    .bulletin-text{
        vertical-align: top;
        margin: 0 4px;
        font-size: 10px;
    }
    .icon-keyboard_arrow_rights{
        position: absolute;
        font-size: 10px;
        right: 12px;
        top: 2px;
    }

   .detail{
        position: fixed;
        z-index: 100;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        overflow: auto;
        background: rgba(7,17,27,0.8);
   }

   .clearfix{
        display: inline-block;
   }
   .clearfix:after{
        display: block;
        content: ".";
        height: 0;
        line-height: 0;
        clear: both;
        visibility: hidden;
   }

   .detail-wrapper{
        min-height: 100%;
        width: 100%;
   }
   .detail-main{
        margin-top: 64px;
        padding-bottom: 64px;
   }
   .detail-close{
        position: relative;
        width: 32px;
        height: 32px;
        margin: -64px auto 0 auto;
        clear: both;
        font-size: 12px;
   }
    .name{
        line-height: 16px;
        text-align: center;
        font-size: 16px;
        font-weight: 700;
    }
</style>