<template>
  <div class="home_page">

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
        msg: 'Hello World!',
        transferObj: {
          isTabbar: false,
          tabbarLink: 'me-info'
        }
      }
    },
    created () {
      this.$emit('transfer', this.transferObj)
      this.$store.commit('setNavigationBarTitle', {title: '我的资料'})
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
