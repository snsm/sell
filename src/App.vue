<template>
  <div id="app">
    <v-header></v-header>
    <div class="tab border-1px">
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

export default {
  components: {
    'v-header':header
  },
}
</script>

<style>
.tab{
    display: flex;
    width: 100%;
    height: 40px;
    line-height: 40px;
    position: relative;
}
.tab-item{
    flex: 1;
    text-align: center;
    -webkit-box-flex: 1;
}

.tab .tab-item > a {
  display: block;
  font-size: 14px;
  color: rgb(77, 85, 93);
}

.tab .tab-item > a.active {
  color: rgb(240, 20, 20)
}

</style>
