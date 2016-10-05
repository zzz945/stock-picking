<!--客户程序必须加scoped属性优先级强制重写f-tabbar-->
<template>
  <div class="weui_tabbar f-tabbar">
    <slot></slot>
  </div>
</template>

<script>
import { parentMixin } from '../../../mixins/multi-items'

export default {
  mixins: [parentMixin],
  props: {
    iconClass: String
  }
}
</script>

<style lang="less">
@import '../../../styles/weui/widget/weui_tab/weui_tab_tabbar';
@import '../../../styles/variable';
.weui_tabbar_icon {
  position: relative;
}
.weui_tabbar_icon > sup {
  position: absolute;
  top: -8px;
  left: 100%;
  transform: translateX(-50%);
  z-index: 101;
}
.f-tabbar {
    font-weight: bold;
    background-color: @theme-color-assist-active;
    &:before {
      border-top: 0px;
    }
  }
</style>
