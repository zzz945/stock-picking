<!--客户程序必须加!important属性优先级强制重写f-group-->
<template>
  <div class="f-group">
    <div class="weui_cells_title" v-if="title" :style="{color:titleColor}" v-html="title"></div>
    <div class="weui_cells" :class="{'f-no-group-title':!title}" :style="{marginTop: gutter}">
      <slot name="after-title"></slot>
      <slot></slot>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    title: String,
    titleColor: String,
    labelWidth: String,
    labelAlign: String,
    labelMarginRight: String,
    gutter: String
  }
}
</script>

<style lang="less" scoped>
  @import '../../../styles/weui/widget/weui_cell/weui_access';
  @import '../../../styles/weui/widget/weui_cell/weui_cell_global';
  @import '../../../styles/variable.less';
  .f-no-group-title {
    margin-top: 15px;
  }
  
  .f-group {
    font-size: 16px;
    .weui_cells_title {
      color: @theme-color;
      background-color: @theme-color-assist;
      font-weight: bold;
      margin: 0;
      padding: .7em .5em .3em .5em;
    }
  }
</style>