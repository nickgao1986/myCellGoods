<template>
  <div class="good">
    <div class="menu_wrapper">
      <ul>
        <li v-for="item in goods" class="menu-item">
          <span class="text border-1px">
            <span v-show="item.type > 0" class="icon" :class="classMap[item.type]"></span>{{item.name}}
          </span>
        </li>
      </ul>
    </div>
    <div class="foods_wrapper">

    </div>
  </div>
</template>

<script type="text/ecmascript-6">
  const ERR_OK = 0;
  export default {
      props: {
          seller: {
              type: Object
          }
      },
      data() {
          return {
              goods: []
          };
      },
      created() {
          this.classMap = ['decrease', 'discount', 'guarantee', 'invoice', 'special'];
          this.$http.get('/api/goods').then((response) => {
            response = response.body;
            if (response.errno === ERR_OK) {
                this.goods = response.data;
            }
          });
      }
  };
</script>

<style lang="stylus" rel="stylesheet/stylus">
  @import "../../common/stylus/mixin.styl"
  @import "../../common/stylus/mixin";
  .good
    display:flex
    position:absolute
    top: 174px
    bottom:46px
    width:100%
    .menu_wrapper
      width: 80px
      flex:0 0 80px
      background: #f3f5f7
      .menu-item
        display:table
        width: 56px
        height: 54px
        padding: 0 12px
        line-height: 14px
        .icon
          display:inline-block
          width: 12px
          height:12px
          vertical-align:top
          margin-right: 2px
          background-size: 12px 12px
          background-repeat:no-repeat
          &.decrease
            bg-image('decrease_3')
          &.discount
            bg-image('discount_3')
          &.guarantee
            bg-image('guarantee_3')
          &.invoice
            bg-image('invoice_3')
          &.special
            bg-image('special_3')
        .text
          display: table-cell
          width: 56px
          vertical-align: middle
          border-1px(rgba(7,17,27,0.1))
          font-size: 12px
    .foods_wrapper
      flex:1
</style>
