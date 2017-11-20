<template>
  <div>
  <hearder-view />
  <br> --------- <br>
  <p v-for="(item, index) in list" :key="index">
    Line:
    <span v-text="item"></span>
  </p>
   <infinite-loading @infinite="infiniteHandler"></infinite-loading>
  </div>
</template>

<script>
import HearderView from './header/index'
import InfiniteLoading from 'vue-infinite-loading'
export default {
  name: 'index',
  data () {
    return {
      list: []
    }
  },
  methods: {
    infiniteHandler ($state) {
      setTimeout(() => {
        const temp = []
        for (let i = this.list.length + 1; i <= this.list.length + 20; i++) {
          temp.push(i)
        }
        this.list = this.list.concat(temp)
        $state.loaded()
      }, 3000)
    }
  },
  components: {
    HearderView,
    InfiniteLoading
  }
}
</script>
