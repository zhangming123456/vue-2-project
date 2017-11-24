<template>
  <div id="app">
    <router-view @transfer='transferFun'></router-view>
    <tabbar v-if="transferObj.isTabbar">
      <tabbar-item :selected="transferObj.tabbarLink === 'home'" link="/">
        <img slot="icon" src="../assets/icon/nav_form.png">
        <img slot="icon-active" src="../assets/icon/nav_form_active.png">
        <span slot="label">报表</span>
      </tabbar-item>
      <tabbar-item :selected="transferObj.tabbarLink === 'order'" link="/order">
        <img slot="icon" src="../assets/icon/nav_order.png">
        <img slot="icon-active" src="../assets/icon/nav_order_active.png">
        <span slot="label">点餐</span>
      </tabbar-item>
      <tabbar-item :selected="transferObj.tabbarLink === 'report'" link="/report">
        <img slot="icon" src="../assets/icon/nav_report.png">
        <img slot="icon-active" src="../assets/icon/nav_report_active.png">
        <span slot="label">订单</span>
      </tabbar-item>
      <tabbar-item :selected="transferObj.tabbarLink === 'me'" link="/me">
        <img slot="icon" src="../assets/icon/nav_me.png">
        <img slot="icon-active" src="../assets/icon/nav_me_active.png">
        <span slot="label">我</span>
      </tabbar-item>
    </tabbar>
  </div>
</template>

<script>
  import { Tabbar, TabbarItem } from 'vux'

  export default {
    components: {
      Tabbar,
      TabbarItem
    },
    name: 'app',
    data () {
      return {
        data: {},
        transferObj: {
          isTabbar: false,
          tabbarLink: 'home',
          backgroundColor: '#FFF'
        }
      }
    },
    created () {
      console.log(this, '---------')
      this.$vux.alert.show({
        title: '提示',
        content: '用户未登录',
        onShow () {
//            _this.$router.go('baidu.com')
        },
        onHide () {
//            _this.$router.go(-1) // 没有token值 用户未登录跳回上一个页面
        }
      })
    },
    methods: {
      transferFun (a) {
        this.transferObj = a
      }
    }
  }
</script>
<style lang='less'>
  @import '../static/libs/css/reset.css';
  @import '../static/libs/css/common.less';
  @import './styles/iconfont/iconfont.css';
  @import '~vux/src/styles/reset.less';
  @import '~vux/src/styles/1px.less';
  @import '~vux/src/styles/close.less';

  #app {
    width: 100%;
    height: 100%;
    .weui-tabbar {
      position: fixed;
    }
  }
</style>
