<template>
    <f-scroll-nav :list="items"></f-scroll-nav>
</template>

<script>
import { FScrollNav } from '../components'
export default {
  components: {
    FScrollNav
  },
  data () {
    return {
      items: [{title: 'item1', link: '/flatui/f-button'},
        {title: 'item2', link: '/flatui/f-divider'},
        {title: 'item3', link: '/flatui/f-button'},
        {title: 'item4', link: '/flatui/f-divider'},
        {title: 'item5', link: '/flatui/f-button'},
        {title: 'item6', link: '/flatui/f-divider'},
        {title: 'item7', link: '/flatui/f-button'},
        {title: 'item8', link: '/flatui/f-divider'},
        {title: 'item9', link: '/flatui/f-button'},
        {title: 'item10', link: '/flatui/f-divider'}]
    }
  }
}
</script>