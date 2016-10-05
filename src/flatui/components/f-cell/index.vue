<!--客户程序必须加!important属性优先级强制重写f-cell-->
<template>
  <div class="weui_cell f-cell" @click="onClick">
    <div class="weui_cell_hd">
      <slot name="icon"></slot>
    </div>
    <div class="weui_cell_bd" :class="{'weui_cell_primary':primary==='title'}">
      <p>
        {{title}}
        <slot name="after-title"></slot>
      </p>
      <inline-desc>{{inlineDesc}}</inline-desc>
    </div>
    <div class="weui_cell_ft" :class="{'weui_cell_primary':primary==='content', 'with_arrow': isLink || !!link}">
      {{value}}
      <slot name="value"></slot>
      <slot></slot>
    </div>
    <slot name="child"></slot>
  </div>
</template>

<script>
import InlineDesc from '../f-inline-desc'
import { go } from '../../../libs/router'

export default {
  components: {
    InlineDesc
  },
  props: {
    title: String,
    value: [String, Number],
    inlineDesc: [String, Number],
    primary: {
      type: String,
      default: 'title'
    },
    link: {
      type: [String, Object]
    }
  },
  methods: {
    onClick () {
      go(this.link, this.$router)
    }
  }
}
</script>

<style lang="less" scoped>
  @import '../../../styles/variable.less';
  @import '../../../styles/weui/widget/weui_cell/weui_cell_global';
  div.f-cell {
    background-color: @theme-color;
    &:not(.no_access) {
      // 在cell_access和其它类型的cell混着用的场景下，其它cell要加no_access，避免有点击态
      .setTapColor;
      &:active {
        background-color: @theme-color-active;
      }
    }
    font-weight: bold;
    i {
      margin-right: 10px;
      color: @theme-color-assist;
    }
    p {
      color: @theme-color-text;
    }
    &:before {
      border-top: 10px solid @theme-color-active;
      height: 10px;
      left: 0px;
    }
    .weui_cell_ft {
      color: @theme-color-text;
      &.with_arrow:after {
        content: " ";
        display: inline-block;
        transform: rotate(45deg);
        height: 6px;
        width: 6px;
        border-width: 4px 4px 0 0;
        border-color: @theme-color-text;
        border-style: solid;
        position: relative;
        top: -1px;
        margin-left: .3em;
      }
    }
    .vux-label-desc {
      color: @theme-color-assist;
    }
  }
</style>