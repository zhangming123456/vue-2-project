<template>
  <div class="me_page">
    <div v-transfer-dom>
      <previewer :list="list" ref="previewer" :options="options"></previewer>
    </div>
    <div class="azm-me" @click="routerLink('/me-info')">
      <div class="azm-me-link clearfix">
        <div class="fl azm-me-link-item azm-me-img">
          <img src="../assets/logo_520.png" alt="" class="">
        </div>
        <div class="fl azm-me-link-item azm-me-name">
          <h3>赵小刀</h3>
        </div>
        <div class="fr azm-me-link-item azm-me-qr">
          <img class="azm-me-img previewer-demo-img" :src="list[0].src" @click="openImg($event,0)">
          <i class="iconfont icon-fanhui-copy-copy-copy azm-icon-arrow-right"></i>
        </div>
      </div>
    </div>
    <div class="azm-cell-list">
      <group class="azm-cell-list-group">
        <cell is-link link="/" title="我的应用" class="azm-cell">
          <i slot="icon" class="iconfont icon-05 azm-icon azm-icon-34c9e1"></i>
        </cell>
        <cell is-link title="我的账号" class="azm-cell">
          <i slot="icon" class="iconfont icon-zuanshi azm-icon azm-icon-f86162"></i>
          <div>收银账号设置</div>
        </cell>
        <cell is-link link="/me-shop" title="商家开店" class="azm-cell">
          <i slot="icon" class="iconfont icon-shangjia azm-icon azm-icon-41a3fb"></i>
        </cell>
        <cell is-link title="修改密码" class="azm-cell">
          <i slot="icon" class="iconfont icon-mima azm-icon azm-icon-ac92eb"></i>
        </cell>
        <cell is-link title="联系客服" class="azm-cell">
          <i slot="icon" class="iconfont icon-kefu azm-icon azm-icon-febf00"></i>
        </cell>
      </group>
    </div>
  </div>
</template>

<script>
  import { Group, Cell, CellBox, Previewer, TransferDom } from 'vux'

  export default {
    directives: {
      TransferDom
    },
    components: {
      Group,
      Cell,
      CellBox,
      Previewer
    },
    data () {
      return {
        socketService: null,
        msg: 'Hello World!',
        setData: null,
        transferObj: {
          isTabbar: true,
          tabbarLink: 'me'
        },
        list: [
          {
            src: '../../assets/qr.png'
          }
        ],
        options: {
          getThumbBoundsFn (index) {
            // find thumbnail element
            let thumbnail = document.querySelectorAll('.previewer-demo-img')[index]
            // get window scroll Y
            let pageYScroll = window.pageYOffset || document.documentElement.scrollTop
            // optionally get horizontal scroll
            // get position of element relative to viewport
            let rect = thumbnail.getBoundingClientRect()
            // w = width
            return {x: rect.left, y: rect.top + pageYScroll, w: rect.width}
            // Good guide on how to get element coordinates:
            // http://javascript.info/tutorial/coordinates
          }
        }
      }
    },
    created () {
      this.$emit('transfer', this.transferObj)
      this.$store.commit('setNavigationBarTitle', {title: '个人中心'})
    },
    methods: {
      openImg (e, index) {
        this.$refs.previewer.show(index)
        e.cancelBubble = true
      },
      routerLink (path, params) {
        this.$router.push({path, params})
      }
    }
  }
</script>
<style scoped lang='less'>
  .me_page {
    background-color: #fff;
    padding-bottom: 120px;
  }

  .azm-me {
    .azm-me-link {
      display: block;
      box-sizing: border-box;
      padding: 20px 30px 0 50px;
      line-height: 76px;
      .azm-me-name {
        h3 {
          font-size: 15px;
          color: #34c9e1;
          font-weight: 600;
        }
      }
      .azm-me-link-item {
        height: 100%;
      }
      .azm-me-link-item.azm-me-img {
        width: 65px;
        height: 65px;
        margin-right: 36px;
        text-align: center;
        vertical-align: middle;
        border-radius: 100%;
        border: 5px solid #efefef;
        overflow: hidden;
        img {
          width: 60px;
          height: auto;
        }
      }
      .azm-me-qr {
        img {
          width: 30px;
          height: auto;
          vertical-align: middle;
          margin-right: 12px;
        }
        .azm-icon-arrow-right {
          font-size: 12px;
          width: 14px;
          height: 100%;
          color: #C8C8CD;
        }
      }
    }
  }

  .azm-cell-list {
    padding-left: 20px;
    padding-right: 20px;
    .azm-cell {
      font-size: 13px;
      color: #2b2e3a;
      .azm-icon {
        width: 35px;
        height: 30px;
        line-height: 30px;
        font-size: 17px;
        font-weight: bold;
      }
      .azm-icon-34c9e1 {
        color: #34c9e1;
      }
      .azm-icon-f86162 {
        color: #f86162;
      }
      .azm-icon-41a3fb {
        color: #41a3fb;
      }
      .azm-icon-ac92eb {
        color: #ac92eb;
      }
      .azm-icon-febf00 {
        color: #febf00;
      }
      .azm-icon-48cfae {
        color: #48cfae;
      }
    }
  }


</style>
