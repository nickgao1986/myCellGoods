<template>
  <div class="ratings">
    <div class="ratings-content">
      <div class="overview">
        <div class="overview-left">
          <h1 class="score">{{seller.score}}</h1>
          <div class="title">综合评分</div>
          <div class="rank">高于周边商家{{seller.rankRate}}%</div>
        </div>
        <div class="overview-right"></div>
      </div>
    </div>
  </div>
</template>

<script type="text/ecmascript-6">
  export default {
      props: {
          seller: {
              type: Object
          }
      }
  };
</script>

<style lang="stylus" rel="stylesheet/stylus">
  @import "../../common/stylus/mixin.styl"

  .ratings
    position:absolute
    top: 174px
    bottom:0px
    width:100%
    overflow: hidden
    .overview
      display flex
      padding 18px 0
      .overview-left
        flex 0 0 137px
        width 137px
        border-right 1px solid rgba(7,17,27,0.2)
        text-align center
        .score
          font-size 24px
          color rgb(255,153,0)
          line-height 28px
        .title
          font-size 12px
          line-height 12px
          color rgb(7,17,27)
          margin-top 6px
        .rank
          font-size 10px
          line-height 10px
          color rgb(7,17,27)
          margin-top 8px
      .overview-right
        flex 1
        padding-left 24px

</style>
