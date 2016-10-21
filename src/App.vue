<template>
  <div class="app-bd">
    <loading :show="isLoading" position="absolute"></loading>
    <view-box v-ref:view-box>
      <!--header slot-->
      <div class="header-box" slot="header">
        <f-header class="flat-header" :left-options="leftOptions" :transition="headerTransition" :title="title" @on-click-title="scrollTop"></f-header>
      </div>
      <!--default slot-->
      <router-view :transition="'vux-pop-' + (direction === 'forward' ? 'in' : 'out')"></router-view>
      <!--bottom slot-->
      <f-tabbar v-show="!isTabbarDemo" slot="bottom">
        <f-tabbar-item v-link="{path:'/'}" :selected="route.path === '/'">
          <i slot="icon" class="fa fa-home fa-lg"></i>
          <span slot="label">Home</span>
        </f-tabbar-item>
        <f-tabbar-item v-link="{path:'/demo'}" :selected="isDemo" badge="9">
          <i slot="icon" class="fa fa-dashcube fa-lg"></i>
          <span slot="label">Demos</span>
        </f-tabbar-item>
        <f-tabbar-item v-link="{path:'/flatui'}" :selected="isFlatuiDemo">
          <i slot="icon" class="fa fa-windows fa-lg"></i>
          <span slot="label">Flatui demos</span>
        </f-tabbar-item>
        <f-tabbar-item v-link="{path:'/project/donate'}" :selected="route.path === '/project/donate'" show-dot>
          <i slot="icon" class="fa fa-money fa-lg"></i>
          <span slot="label">Donate</span>
        </f-tabbar-item>
      </f-tabbar>
    </view-box>
  </div>
</template>

<script>
import store from './vuex/store'
import { Loading, ViewBox } from './components'
import { FTabbar, FTabbarItem, FHeader } from './flatui/components'
import Vconsole from 'vconsole'

export default {
  components: {
    FTabbar,
    FTabbarItem,
    Loading,
    ViewBox,
    FHeader,
    Vconsole
  },
  store: store,
  vuex: {
    getters: {
      route: (state) => state.route,
      isLoading: (state) => state.isLoading,
      direction: (state) => state.direction
    }
  },
  data () {
    return {
      routerTransition: {
        forward: 'slideRL',
        back: 'slideLR'
      }
    }
  },
  methods: {
    scrollTop () {
      this.$refs.viewBox.$els.viewBoxBody.scrollTop = 0
    }
  },
  computed: {
    leftOptions () {
      return {
        showBack: this.route.path !== '/'
      }
    },
    headerTransition () {
      return this.direction === 'forward' ? 'vux-header-fade-in-right' : 'vux-header-fade-in-left'
    },
    componentName () {
      const parts = this.route.path.split('/')
      if (/component/.test(this.route.path) && parts[2]) return parts[2]
    },
    isDemo () {
      return /component|demo/.test(this.route.path)
    },
    isFlatuiDemo () {
      return /flatui/.test(this.route.path)
    },
    isTabbarDemo () {
      return /tabbar/.test(this.route.path)
    },
    title () {
      if (this.route.path === '/') return 'Home'
      if (this.route.path === '/project/donate') return 'Donate'
      if (this.route.path === '/demo') return 'Demo list'
      return this.componentName ? `Demo/${this.componentName}` : 'Demo/~~'
    }
  }
}
</script>

<style lang="less">
  @import 'styles/index.less';
  @import './styles/variable';
  html,
  body {
    height: 100%;
    width: 100%;
    overflow-x: hidden;
  }
  /* v-r-transition, default is {forward: 'forward', back: 'back'}*/
  
  .forward-enter,
  .forward-leave {
    transform: translate3d(-100%, 0, 0);
  }
  
  .back-enter,
  .back-leave {
    transform: translate3d(100%, 0, 0);
  }
  
  .app-bd {
    height: 100%;
    width: 100%;
    .f-header {
      z-index: 100!important;
      height: 32px!important;
      font-size: 16px!important;
      left: 0!important;
      top: 0!important;
    }
    .weui_tab_bd {
      padding-top: 32px!important;
    }
  }
  /**
* vue-router transition
*/
  
  .vux-pop-out-transition,
  .vux-pop-in-transition {
    width: 100%;
    animation-duration: 0.5s;
    animation-fill-mode: both;
    backface-visibility: hidden;
  }
  
  .vux-pop-out-enter,
  .vux-pop-out-leave,
  .vux-pop-in-enter,
  .vux-pop-in-leave {
    will-change: transform;
    height: 100%;
    position: absolute;
    left: 0;
  }
  
  .vux-pop-out-enter {
    animation-name: popInLeft;
  }
  
  .vux-pop-out-leave {
    animation-name: popOutRight;
  }
  
  .vux-pop-in-enter {
    perspective: 1000;
    animation-name: popInRight;
  }
  
  .vux-pop-in-leave {
    animation-name: popOutLeft;
  }
  
  @keyframes popInLeft {
    from {
      transform: translate3d(-100%, 0, 0);
    }
    to {
      transform: translate3d(0, 0, 0);
    }
  }
  
  @keyframes popOutLeft {
    from {
      transform: translate3d(0, 0, 0);
    }
    to {
      transform: translate3d(-100%, 0, 0);
    }
  }
  
  @keyframes popInRight {
    from {
      transform: translate3d(100%, 0, 0);
    }
    to {
      transform: translate3d(0, 0, 0);
    }
  }
  
  @keyframes popOutRight {
    from {
      transform: translate3d(0, 0, 0);
    }
    to {
      transform: translate3d(100%, 0, 0);
    }
  }
</style>