<template>
  <div class="me_shop_info_page">
    <h2>填写基本资料</h2>
    <group class="me_shop_group">
      <x-input title="门店名称" class="azm-font-cell" label-width=".88rem" v-model="nikeName" is-type="china-name"
               placeholder="请输入门店名称"></x-input>
      <x-input title="分店名称" type="number" class="azm-font-cell" label-width=".88rem" v-model="jobNumber"
               placeholder="请输入分店名称"></x-input>
      <x-input title="门店电话" class="azm-font-cell" label-width=".88rem" name="mobile" mask="9999-999999"
               placeholder="请输入门店电话"
               v-model="Phone" keyboard="number"
               :max="14"
               is-type="china-mobile"></x-input>
    </group>
    <group title="门店设置" class="me_shop_group">
      <popup-picker title="门店类型" class="azm-font-cell" label-width=".88rem" :data="orderList" v-model="orderValue"
                    @on-show="onShow"
                    @on-hide="onHide"
                    @on-change="onChange" placeholder="请选择门店类型"></popup-picker>
      <popup-picker title="业态" class="azm-font-cell" label-width=".88rem" :data="orderList" v-model="orderValue"
                    @on-show="onShow"
                    @on-hide="onHide"
                    @on-change="onChange" placeholder="请选择业态"></popup-picker>
      <x-address title="地址选择" class="azm-font-cell" label-width="1.07rem" v-model="addressValue" raw-value
                 :list="addressData" placeholder="请选择门店地址"
                 value-text-align="right"></x-address>
      <x-textarea title="详细信息" class="azm-font-cell" placeholder="请填写详细信息" :show-counter="false"
                  :rows="3"></x-textarea>
    </group>
    <footer>
      <x-button type="primary" class="azm-font-cell" :show-loading="isSubmit" style="border-radius:99px;">保存</x-button>
    </footer>
  </div>
</template>

<script>
  import {
    Group,
    Cell,
    CellBox,
    XInput,
    XAddress,
    XTextarea,
    XNumber,
    XButton,
    PopupPicker,
    numberComma,
    numberPad,
    numberRandom,
    ChinaAddressData
  } from 'vux'

  export default {
    directives: {
      numberComma,
      numberPad,
      numberRandom
    },
    components: {
      XNumber,
      XTextarea,
      XButton,
      XAddress,
      Group,
      Cell,
      CellBox,
      XInput,
      PopupPicker
    },
    data () {
      return {
        msg: 'Hello World!',
        transferObj: {
          isTabbar: false,
          tabbarLink: 'me-shop'
        },
        nikeName: '',
        orderList: [['sssjj']],
        orderValue: [],
        jobNumber: null,
        Phone: '',
        CharacterList: [['sssjj']],
        Character: [],
        minWipeZero: '',
        maxWipeZero: '',
        minPercentage: '',
        maxPercentage: '',
        isRefund: 0,
        isAntiCheckout: 0,
        isSubmit: false,
        addressData: ChinaAddressData,
        addressValue: []
      }
    },
    created () {
      this.$emit('transfer', this.transferObj)
      this.$store.commit('setNavigationBarTitle', {title: '商家开店'})
    },
    methods: {
      openImg (e, index) {
        this.$refs.previewer.show(index)
        e.cancelBubble = true
      },
      routerLink (path, params) {
        this.$router.push({path, params})
      },
      onShow () {},
      onHide () {},
      onChange () {}
    }
  }
</script>
<style scoped lang='less'>
  .me_shop_info_page {
    box-sizing: border-box;
    h2 {
      text-align: center;
      padding: 10px 0 0;
      font-size: 17px;
      font-weight: 400;
      color: #000;
    }
    .me_shop_group {
      margin-top: -10px;
      &:nth-of-type(2) {
        margin-top: 10px;
      }
      div {
        font-size: 13px;
        color: #000;
      }
      .azm-cellBox {
        padding-top: 0;
        padding-bottom: 0;
      }
    }
    footer {
      .azm-font-cell {
        font-size: 15px;
        font-weight: 400;
      }
      box-sizing: border-box;
      padding: 50px 80px;
    }
  }
</style>
