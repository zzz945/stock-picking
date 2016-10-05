<template>
  <div>
    <tabbar class="flat-tabbar">
      <tabbar-item class="flat-tabbar-item">
        <i slot="icon" class="fa fa-weixin fa-lg"></i>
        <span slot="label">Wechat</span>
      </tabbar-item>
      <tabbar-item class="flat-tabbar-item" show-dot>
        <i slot="icon" class="fa fa-file-text fa-lg"></i>
        <span slot="label">Message</span>
      </tabbar-item>
      <tabbar-item class="flat-tabbar-item" selected>
        <i slot="icon" class="fa fa-internet-explorer fa-lg"></i>
        <span slot="label">Explore</span>
      </tabbar-item>
      <tabbar-item class="flat-tabbar-item">
        <i slot="icon" class="fa fa-navicon fa-lg"></i>
        <span slot="label">News</span>
      </tabbar-item>
    </tabbar>
  </div>
</template>

<script>
import { Tabbar, TabbarItem } from '../components'

export default {
  components: {
    Tabbar,
    TabbarItem
  }
}
</script>
