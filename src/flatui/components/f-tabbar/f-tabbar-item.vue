<!--客户程序必须加scoped属性优先级强制重写f-tabbar-item-->
<template>
  <a href="javascript:;" class="weui_tabbar_item f-tabbar-item" :class="{'weui_bar_item_on': $parent.index === index}" @click="onItemClick">
    <div class="weui_tabbar_icon" :class="[iconClass || $parent.iconClass, {'vux-reddot': showDot}]">
      <slot name="icon"></slot>
      <sup><badge v-if="badge" :text="badge"></badge></sup>
    </div>
    <p class="weui_tabbar_label">
      <slot name="label"></slot>
    </p>
  </a>
</template>

<script>
import { childMixin } from '../../../mixins/multi-items'
import { go } from '../../../libs/router'
import Badge from '../../../components/badge'

export default {
  components: {
    Badge
  },
  mixins: [childMixin],
  props: {
    showDot: {
      type: Boolean,
      default: false
    },
    badge: String,
    link: [String, Object],
    iconClass: String
  },
  events: {
    'on-item-click': function () {
      go(this.link, this.$router)
    }
  }
}
</script>
<style lang="less">
  @import '../../../styles/variable';
  .f-tabbar-item {
    span {
      color: @theme-color-text;
    }
    i {
      color: @theme-color-text;
    }
    &.weui_bar_item_on {
      span {
        color: @theme-color;
      }
      i {
        color: @theme-color;
      }
    }
  }
</style>