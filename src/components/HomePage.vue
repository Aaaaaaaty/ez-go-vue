<template>
  <div>
    <mt-swipe :show-indicators="false" id="swiper">
      <mt-swipe-item v-bind:class="swiperArr[0]"></mt-swipe-item>
      <mt-swipe-item v-bind:class="swiperArr[1]"></mt-swipe-item>
      <mt-swipe-item v-bind:class="swiperArr[2]"></mt-swipe-item>
    </mt-swipe>
    <mt-navbar v-model="activeContainer">
      <mt-tab-item id="1">新鲜的</mt-tab-item>
      <mt-tab-item id="2">附近的</mt-tab-item>
    </mt-navbar>
    <mt-tab-container v-model="activeContainer">
      <mt-tab-container-item id="1">
        <ul id="example-1">
          <li v-for="item in items">
            {{ item.message }}
          </li>
        </ul>
      </mt-tab-container-item>
      <mt-tab-container-item id="2">
        <ul id="example-1">
          <li v-for="item in items">
            {{ item.message }}
          </li>
        </ul>
      </mt-tab-container-item>
    </mt-tab-container>
    <mt-tabbar v-model="selectedTabbar" :fixed="true">
      <mt-tab-item id="home">
        <img slot="icon" src="../assets/logo.png">
        外卖
      </mt-tab-item>
      <mt-tab-item id="area">
        <img slot="icon" src="../assets/logo.png">
        订单
      </mt-tab-item>
      <mt-tab-item id="msg">
        <img slot="icon" src="../assets/logo.png">
        发现
      </mt-tab-item>
      <mt-tab-item id="me">
        <img slot="icon" src="../assets/logo.png">
        我的
      </mt-tab-item>
    </mt-tabbar>
  </div>
</template>

<script>
  import server from '../util/host.js'
  export default {
    data: function () {
      return {
        swiperArr: ['swiper-item0', 'swiper-item1', 'swiper-item2'],
        activeContainer: '1',
        selectedTabbar: 'home',
        items: [
          { message: 'Foo' },
          { message: 'Bar' }
        ]
      }
    },
    created: function() {
      console.log(this)
      this.$http.post(server.host + '/getNearProducts', {}).then((res) => {
        console.log(res.body)
      })
    }
  }
</script>

<style scoped>
  #swiper {
    width: 7.5rem;
    height: 4rem;
  }
  .diva {
    width: 7.5rem;
    height: 5rem;
    background-color: red;
  }
  .swiper-item0 {
    background: url('http://lofter.nos.netease.com/sogou-eWVYeVFFSGk4QmlwZDdpdUJ2bndvWFZ3b3ZESU9rZExWSW93eWtCY3FpcVlobjVDNFJvTG4tSUVfRWpNRXBKcQ.jpg') center no-repeat;
    background-size: cover;
  }
  .swiper-item1 {
    background: url('http://lofter.nos.netease.com/sogou-dWtiblRvbTFKUXpYUFpjX0NXOFkwMHYyVjhmcldRbmhfMFFVcjJlSHJXODlZeEdRYlBKRFVyN0prLVFYOXY4Qw.jpg') center no-repeat;
    background-size: cover;
  }
  .swiper-item2 {
    background: url('http://lofter.nos.netease.com/sogou-R3lEeGI0RTdkU1hDRk44Yk5SWVJ2LUZENV9TYmFibER3TzYzYUI0VTY4UEhCVmE0SWdjM1FGekhVcHBpc0hIag.jpg') center no-repeat;
    background-size: cover;
  }
</style>
