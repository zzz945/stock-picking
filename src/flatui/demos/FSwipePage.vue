<template>
    <div>
        <swiper v-ref:swiper direction="horizontal" :mousewheel-control="true" :performance-mode="false" :pagination-visible="true"
            :pagination-clickable="true" @slide-change-start="onSlideChangeStart" @slide-change-end="onSlideChangeEnd">
            <div>Page 1</div>
            <div>Page 2</div>
            <div>Page 3</div>
            <div>Page 4</div>
            <div>{{{page5}}}</div>
            <div>Page 6</div>
            <div>Page 7</div>
            <div>Page 8</div>
        </swiper>
        <f-button @click="nextPage()">next</f-button>
        <f-button @click="prevPage()">prev</f-button>
        <f-button @click="setPage(5)">page5 ajax</f-button>
    </div>
</template>

<script>
import { FButton } from '../components'
import Swiper from 'vue-swiper'

export default {
  components: {
    FButton,
    Swiper
  },
  data () {
    return {
      page5: 'Page 5'
    }
  },
  methods: {
    nextPage () {
      this.$refs.swiper.next()
    },
    prevPage () {
      this.$refs.swiper.prev()
    },
    setPage (p) {
      this.page5 = '<p style="color:red;">改变了内容，可以ajax</p>'
      this.$refs.swiper.setPage(p)
    },
    onSlideChangeStart (currentPage) {
      console.log('onSlideChangeStart', currentPage)
    },
    onSlideChangeEnd (currentPage) {
      console.log('onSlideChangeEnd', currentPage)
    }
  }
}
</script>

<style>
    .swiper {
        height: 200px;
        margin-bottom: 80px;
    }
    
    .swiper-wrap > div {
        display: flex;
        justify-content: center;
        align-items: center;
        text-align: center;
        font-size: 48px;
        color: #fff;
    }
    
    .swiper-wrap > div:nth-child(3n) {
        background-color: skyblue;
    }
    
    .swiper-wrap > div:nth-child(3n + 1) {
        background-color: yellowgreen;
    }
    
    .swiper-wrap > div:nth-child(3n + 2) {
        background-color: rosybrown;
    }
</style>