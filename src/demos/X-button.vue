<template>
  <div class="button-demo">
    <divider>default</divider>
    <box gap="10px 10px">
      <x-button>submit</x-button>
      <x-button type="primary">primary</x-button>
      <x-button type="warn">Delete</x-button>
      <x-button type="flat" class="flat-button">
        <span class="fa-stack fa-lg">
          <i class="fa fa-square-o fa-stack-2x"></i>
          <i class="fa fa-twitter fa-stack-1x"></i>
        </span>&nbsp;flat
      </x-button>

      <divider>mini</divider>
      <x-button mini>submit</x-button>
      <x-button mini type="primary">primary</x-button>
      <x-button mini type="warn">Delete</x-button>
      <x-button mini type="flat" class="flat-button">flat</x-button>
      <br>
      <x-button mini plain>submit</x-button>
      <x-button mini plain type="primary">primary</x-button>

      <divider>plain</divider>
      <x-button plain>submit</x-button>
      <x-button plain type="primary">primary</x-button>

      <divider>disabled</divider>
      <x-button disabled>disable submit</x-button>
      <x-button type="primary" disabled>disable primary</x-button>
      <x-button type="warn" disabled>disable Delete</x-button>
      <x-button type="flat" disabled class="flat-button">disable flat</x-button>

      <divider>use :text and :disabled</divider>
      <x-button :text="submit001" :disabled="disable001" @click="processButton001" type="primary"></x-button>

      <divider>combined with flexbox</divider>
      <flexbox>
        <flexbox-item>
          <x-button type="primary">primary</x-button>
        </flexbox-item>
        <flexbox-item>
          <x-button type="warn">Delete</x-button>
        </flexbox-item>
        <flexbox-item>
          <x-button type="flat" class="flat-button">flat</x-button>
        </flexbox-item>
      </flexbox>
      <divider>combined with flexbox</divider>
      <flexbox>
        <flexbox-item>
          <x-button type="default">default</x-button>
        </flexbox-item>
        <flexbox-item>
          <x-button type="primary">primary</x-button>
        </flexbox-item>
        <flexbox-item>
          <x-button type="warn">Delete</x-button>
        </flexbox-item>
        <flexbox-item>
          <x-button type="flat" class="flat-button">flat</x-button>
        </flexbox-item>
      </flexbox>

    </box>

  </div>
</template>

<script>
import { XButton, Box, GroupTitle, Group, Flexbox, FlexboxItem, Divider } from '../components'

export default {
  components: {
    XButton,
    Box,
    GroupTitle,
    Group,
    Flexbox,
    FlexboxItem,
    Divider
  },
  methods: {
    change (value) {
      console.log('change:', value)
    },
    processButton001 () {
      this.submit001 = 'processing'
      this.disable001 = true
    }
  },
  data () {
    return {
      submit001: 'click me',
      disable001: false
    }
  }
}
</script>

<style lang="less" scoped>
  @import '../styles/variable';
  .flat-button {
    font-weight: bold;
    background-color: @theme-color-assist;
    &:not(.weui_btn_disabled):active {
      background-color: @theme-color-assist-active;
    }
  }

  .button-demo {
    background-color: @theme-color-disable;
  }
</style>