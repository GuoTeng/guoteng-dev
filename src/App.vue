<template>
  <div id="app">
    <myHeader :seller="seller"></myHeader>
    <div class="tab">
      <div class="item"><router-link to="/goods">商品</router-link></div>
      <div class="item"><router-link to="/ratings">评分</router-link></div>
      <div class="item"><router-link to="/seller">商家</router-link></div>
    </div>
    <router-view></router-view>
  </div>
</template>

<script>
import myHeader from '@/components/myHeader/myHeader'


export default {
  name: 'app',
  components: {
    myHeader: myHeader
  },
  data() {
    return {
      seller: {}
    }
  },
  created() {
    this.$axios.get('./test/data.json').then((response) => {
      this.seller = response.data.seller;
    });
  },
}
</script>

<style type="text/css" lang="scss">
#app {
  font-family: 'Microsoft YaHei','Avenir', Helvetica, Arial, sans-serif;

  .tab {
    display: flex;
    .item {
      flex: 1;
      text-align: center;
    }
  }
}
</style>
