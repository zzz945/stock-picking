<!--客户程序必须加!important属性优先级强制重写f-button-->
<template>
  <button :class="classes" :disabled="disabled">
    <slot></slot>
  </button>
</template>

<script>
export default {
  props: {
    disabled: Boolean,
    icon: Boolean,
    block: Boolean
  },
  computed: {
    classes () {
      let ret = 'weui_btn f-button'
      if (this.disabled) ret += ' weui_btn_disabled'
      if (this.icon) ret += ' f-icon'
      if (this.block) ret += ' block'
      return ret
    }
  }
}
</script>

<style lang="less" scoped>
  @import '../../../styles/variable.less';
  @import '../../../styles/weui/widget/weui_button/weui_button.less';
  button.f-button {
    background-color: @theme-color;
    font-weight: bold;
    &:not(.weui_btn_disabled):visited {
      color: @theme-color-text;
    }
    &:not(.weui_btn_disabled):active {
      color: @theme-color-text-active;
      background-color: @theme-color-active;
    }
  }
  
  button.f-icon {
    border-radius: 100%;
    width: 100px;
    height: 100px;
    margin: 10px;
    &:after {
      border: 0px;
    }
  }
  
  button.block {
    display: inline-block;
    width: 100px;
  }
</style>