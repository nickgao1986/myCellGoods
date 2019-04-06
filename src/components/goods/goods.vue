<template>
  <div class="good">
    <div class="menu_wrapper">
      <ul>
        <li v-for="item in goods">
          <span class="text">
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
                console.log(this.goods);
            }
          });
      }
  };
</script>

<style lang="stylus" rel="stylesheet/stylus">
  @import "../../common/stylus/mixin.styl"
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
    .foods_wrapper
      flex:1
</style>
