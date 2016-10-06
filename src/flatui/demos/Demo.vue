<template>
  <div>
    <f-group title="Form">
      <f-cell title="f-button" link="flatui/f-button">
        <span class="demo-icon" slot="icon">&#xe61b;</span>
      </f-cell>
      <f-cell title="f-divider" link="flatui/f-divider">
        <span class="demo-icon" slot="icon">&#xe65d;</span>
      </f-cell>
      <f-cell title="f-page-nav" link="flatui/f-page-nav">
        <span class="demo-icon" slot="icon">&#xe65d;</span>
      </f-cell>
    </f-group>
  </div>
</template>

<script>
import { FCell, FGroup } from '../components'

export default {
  components: {
    FCell,
    FGroup
  },
  data () {
    return {
    }
  }
}
</script>

<style lang="less">
  @import '../../styles/variable';
  .center {
    margin-top: 15px;
    text-align: center;
  }
  
  .firefox .weui_cells:after {
    transform-origin: 50% 50%;
  }
  
  .demo-icon {
    color: @theme-color-assist;
  }
</style>