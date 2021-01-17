<template>
  <ul class="carousel">
      <li v-for="item in items" v-if="item.type == selectFilter || selectFilter == 'all'">
        <div >
          <item :item="item" />
        </div>  
      </li>
  </ul>
</template>
<script>
import axios from 'axios';
import Item from './Item.vue'
export default {
  components: {
    Item,
  },
  props: {
    selectFilter: String,
  },
  data() {
    return {
      items: '',
      item: '',
    }
  },
  created() {
     this.$nuxt.$on('filterWasSelected', (data) => {
      this.selectFilter = data;
   })
  
    axios.get('/api/getJSON').then(res => {
      const data = res.data.carouselData.shelf;
      // console.log(res.data.carouselData.shelf[1]);
      // console.log('\!!!!/');
      // console.log(res.data.carouselData);
      const elements = [];
      for(let key in data) {
        const element = data[key];
        element.id = key; 
        elements.push(element);
        // elements.push(data[key])
      }
      this.items = elements;
    })
    .catch(error => console.log(error));
  },
  methods: {

  },

}
</script>
 
<style>
* { box-sizing: border-box; }

body { font-family: sans-serif; }

.carousel {
  background: #EEE;
}

.carousel-cell {
  width: 66%;
  height: 200px;
  margin-right: 10px;
  background: #8C8;
  border-radius: 5px;
  counter-increment: gallery-cell;
}

/* cell number */
.carousel-cell:before {
  display: block;
  text-align: center;
  content: counter(gallery-cell);
  line-height: 200px;
  font-size: 80px;
  color: white;
}

</style>
