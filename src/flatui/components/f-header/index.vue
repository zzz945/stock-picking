<template>
  <div class="f-header">
    <div class="f-header-left">
      <div class="left-arrow" @click="onClickBack" v-show="leftOptions.showBack" :transition="transition"></div>
      <slot name="left"></slot>
    </div>
    <h1 class="f-header-title" @click="$emit('on-click-title')"><span v-show="title" :transition="transition">{{title}}</span>
      <slot></slot>
    </h1>
    <div class="f-header-right">
      <a class="f-header-more" @click.preventDefault @click="$emit('on-click-more')" v-if="rightOptions.showMore"></a>
      <slot name="right"></slot>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    leftOptions: {
      type: Object,
      default () {
        return {
          showBack: true,
          backText: 'Back',
          preventGoBack: false
        }
      }
    },
    title: String,
    transition: String,
    rightOptions: {
      type: Object,
      default () {
        return {
          showMore: false
        }
      }
    }
  },
  methods: {
    onClickBack () {
      if (this.leftOptions.preventGoBack) {
        this.$emit('on-click-back')
      } else {
        history.back()
      }
    }
  }
}
</script>

<style lang="less" scoped>
  @import '../../../styles/variable.less';
  .f-header {
    position: absolute;
    background-color: @x-header-background-color;
    width: 100%;
    height: 32px;/*重载时注意，必须为2倍font-size*/
    font-size: 16px;
    font-weight: bold;
    .f-header-title {
      position: absolute;
      left: 25%;
      width: 50%;
      height: 2em;
      line-height: 2em;
      text-align: center;
      color: @x-header-title-color;
      font-size: 1em;
    }
    .f-header-left {
      .left-arrow {
        position: absolute;
        width: 2em;
        height: 2em;
        &:before {
          content: "";
          position: absolute;
          width: .5em;
          height: .5em;
          border: .125em solid @x-header-arrow-color;
          border-width: .125em 0 0 .125em;
          transform: rotate(315deg);
          left: .65em;
          top: .65em;
        }
      }
    }
  }
</style>