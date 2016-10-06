<template>
    <div>
        <f-page-nav :page="page" :page-size="pageSize" :total="total" :max-link="maxLink" :page-handler="pageHandler" :create-url="createUrl"></f-page-nav>
    </div>
</template>

<script>
import { FPageNav } from '../components'

export default {
  components: {
    FPageNav
  },
  data () {
    return {
      page: 1, // page
      pageSize: 1, // pageSize,  default is 10
      total: 10, // total item count
      maxLink: 5 // how many links to show, must not less than 5,  default is 5
    }
  },
  methods: {
    pageHandler: function (page) {
      // here you can do custom state update
      this.page = page
      console.log('page=' + page)
    }
  }
}
</script>