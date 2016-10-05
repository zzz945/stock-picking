<!--客户程序必须加!important属性优先级强制重写f-divider-->
<template>
  <p class="f-divider">
    <slot></slot>
  </p>
</template>

<style lang="less" scoped>
  .f-divider {
    display: table;
    white-space: nowrap;
    height: auto;
    overflow: hidden;
    line-height: 1;
    text-align: center;
    padding: 10px 0;
    color: #666;
    font-weight: bold;
    font-size: 18px;
    &:after,
    &:before {
      content: '';
      display: table-cell;
      position: relative;
      top: 50%;
      width: 50%;
      border-bottom: 5px solid #666;
    }
  }
</style>