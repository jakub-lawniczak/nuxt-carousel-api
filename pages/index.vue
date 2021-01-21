<template>
    <section class="task">
        <div class="container-cstm-fluid">
            <items-header />
            <items-filters @filterWasSelected="setFilter" />
        </div> 
        <items-carousel :items="selectedItems"/>  
    </section>
</template>

<script>
import axios from 'axios';
import ItemsHeader from '../components/ItemsHeader.vue'
import ItemsFilters from '../components/ItemsFilters.vue'
import ItemsCarousel from '../components/ItemsCarousel.vue'
export default {
    components: { ItemsCarousel, ItemsHeader, ItemsFilters },
    data() {
        return {
            items: [],
            filter: 'all',
        }
    },
    computed: {
        selectedItems() {
            return this.filter === 'all' ? this.items : this.getFilteredItems();
        },
    },
    async mounted() {
        this.items = await this.fetchData();
    },
    methods: {
        fetchData() {
            return axios.get('/api/getJSON').then(res => res.data.carouselData.shelf);           
        },
        setFilter(value) {
            this.filter = value;
        },
        getFilteredItems() {
            return this.items.filter(item => item.shelf_type === this.filter);
        }
    },
  }
</script>
<style lang="scss">
   .task {
       height: 100vh;
       padding: 64px 0;
       background-color: #e5e5e5;
   }
</style>