<template>
  <div>
    <div class="center">
      <svg style="width:60px;height:60px;" version="1.1" id="图形" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink"
        x="0px" y="0px" width="1024px" height="1024px" viewBox="0 0 1024 1024" enable-background="new 0 0 1024 1024" xml:space="preserve">
        <path class="svgpath" data-index="path_0" fill="#f1c40f" d="M512 816.64 51.2 985.6l460.8-947.2 460.8 947.2L512 816.64 512 816.64zM509.44 207.36 189.44 862.72l317.44-117.76L506.88 207.36 509.44 207.36zM509.44 207.36"
        />
      </svg>

      <h1 class="vux-title" style="display:none;">
        <span class="demo-icon" slot="icon" style="font-size:60px;color:#35495e;display: block;">&#xe637;</span>
      </h1>
      <p class="vux-notice">v{{version}}</p>
    </div>
    <f-group class="flat-group">
      <f-cell title="Demo" link="/demo" value="演示">
        <i slot="icon" class="fa fa-dashcube fa-2x fa-fw"></i>
      </f-cell>
    </f-group>
    <f-group class="flat-group">
      <f-cell title="Flatui demo" link="/flatui" value="演示">
        <i slot="icon" class="fa fa-windows fa-2x fa-fw"></i>
      </f-cell>
    </f-group>
    <f-group class="flat-group">
      <f-cell title="Buy me a coffee" link="project/donate">
        <i slot="icon" class="fa fa-money fa-2x fa-fw"></i>
        <div class="badge-value" slot="value" class="vux-center-v">
          <badge text="捐赠"></badge>
        </div>
      </f-cell>
      <f-cell title="Github" link="http://github.com/airyland/vux" value="Star me">
        <i slot="icon" class="fa fa-github fa-2x fa-fw"></i>
      </f-cell>
    </f-group>
  </div>
</template>

<script>
import { Badge } from './components'
import { FCell, FGroup } from './flatui/components'
const version = require('../package.json').version
export default {
  components: {
    FCell,
    FGroup,
    Badge
  },
  data () {
    return {
      version: version
    }
  }
}
</script>

<style lang="less">
  @import './demos/style.css';
  @import './styles/variable';
  .center {
    margin-top: 15px;
    text-align: center;
  }
  
  .vux-notice {
    color: @theme-color;
    line-height: 40px;
    font-weight: bold;
  }
  
  .vux-title {
    vertical-align: middle;
    text-align: center;
    color: @theme-color-assist;
    display: inline-block;
    width: 75px;
    height: 75px;
    line-height: 75px;
    border-radius: 50%;
    font-weight: bold;
  }
</style>