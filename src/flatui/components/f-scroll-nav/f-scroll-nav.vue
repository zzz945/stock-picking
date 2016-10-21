<template>
    <div class="wrap">
        <div v-bind:class="['tab-item', selected(index) ? 'active-tab-item' : '']" v-for="(index, item) in list">
            <span @click="gotoLink(index)">{{item.title}}</span>
        </div>
    </div>
</template>

<script>
import { Scroller } from '../../../components'
export default {
  components: {
    Scroller
  },
  props: {
    list: {
      type: Array,
      default () {
        return []
      }
    }
  },
  data () {
    return {
      curIdx: true
    }
  },
  ready () {
  },
  methods: {
    gotoLink (index) {
      console.log(event.currentTarget.className)
      this.curIdx = index
      this.$route.router.go(this.list[index].link)
    },
    selected (index) {
      return (index === this.curIdx)
    }
  }
}
</script>
<style lang="less" scoped>
    .wrap {
        width: 200%;
        display: flex;
        .tab-item {
            width: 10%;
            flex-shrink: 0;
            &:active {
                color: red;
            }
        }
        .active-tab-item {
            color: red;
        }
    }
</style>