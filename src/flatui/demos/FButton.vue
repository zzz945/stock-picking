<template>
  <div>
    <f-divider>flat button</f-divider>
    <f-button>
      <i class="fa fa-twitter fa-1g"></i>&nbsp;flat
    </f-button>
    <f-divider>flat button disabled</f-divider>
    <f-button disabled>disable</f-button>
    <f-divider>flat icon button</f-divider>
    <f-button icon><i class="fa fa-twitter fa-3x"></i></f-button>
    <f-divider>flat icon button disabled</f-divider>
    <f-button disabled icon><i class="fa fa-twitter fa-3x"></i></f-button>
    <f-divider>block button</f-divider>
    <f-button block>flat</f-button>
    <f-button block disabled>disable</f-button>
    <f-button block icon><i class="fa fa-twitter fa-3x"></i></f-button>
    <f-button block disabled icon><i class="fa fa-twitter fa-3x"></i></f-button>
  </div>
</template>

<script>
import { FButton, FDivider } from '../components/'
export default {
  components: {
    FButton,
    FDivider
  }
}
</script>

<style lang="less" scoped>
  @import '../../styles/variable';
</style>