<template>
  <div id="app">
    <v-header :seller="seller"></v-header>
    <div class="tab">
      <div class="tab-item">
        <router-link to="/goods">商品</router-link>
      </div>
      <div class="tab-item">
        <router-link to="/ratings">评论</router-link>
      </div>
      <div class="tab-item">
        <router-link to="/seller">商家</router-link>
      </div>
    </div>
    <router-view></router-view>
  </div>
</template>

<script>
import header from './components/header/header'
import goods from 'components/goods/goods'
import geller from 'components/seller/seller'
import ratings from 'components/ratings/ratings'

const ERR_OK = 0;

export default {
  data () {
    return {
      seller: {}
    };
  },
  created() {
      this.$http.get('/api/seller').then((response) => {
        response = response.body;
        if (response.errno === ERR_OK) {
          this.seller = response.data;
          console.log(this.seller);
        }
      });
    },
  components: {
    'v-header':header
  },
}
</script>

<style>
body, html {
    line-height: 1;
    font-weight: 200;
    font-family: 'PingFang SC', 'STHeitiSC-Light', 'Helvetica-Light', arial, sans-serif;
}
.tab{
    display: flex;
    width: 100%;
    height: 40px;
    line-height: 40px;
    border-bottom-style: solid;
    border-bottom-width: 1px;
    border-bottom-color: gainsboro;
}
.tab-item{
    flex: 1;
    text-align: center;
    -webkit-box-flex: 1;
}

.tab .tab-item > a {
  display: block;
  font-size: 14px;
  color: #4d555d;
}

.tab .tab-item > a.active {
  color: #f01414;
}
</style>
