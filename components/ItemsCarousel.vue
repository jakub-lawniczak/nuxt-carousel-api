<template>
  <ul class="carousel">
      <li v-for="item in items">
        <div >
          <item :item="item" />
        </div>  
      </li>
  </ul>
</template>
<script>
import Item from './Item.vue'
export default {
  components: {
    Item,
  },
  props: {
    items: {
      type: Array, 
      default: () => []
    }
  },
  data() {
    return {
    }
  },
  created() {
  //    this.$nuxt.$on('filterWasSelected', (data) => {
  //     this.selectFilter = data;
  //  })

  },
  methods: {

  },

}
</script>
 
<style>
* { box-sizing: border-box; }

body { font-family: sans-serif; }

.carousel {
  /* background: #EEE; */
  display: flex;
}
</style>
