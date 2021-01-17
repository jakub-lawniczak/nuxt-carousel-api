
<template>
    <section class="task">
        <div class="container-cstm-fluid">
            <items-header />
            <items-filters @filterWasSelected="setFilter" />
            <items-carousel :items="selectedItems"/>
        </div>   
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
                filter: 'all',
                items: [],
                selectedItems: this.items,
            }
        },
        created() { 
            axios.get('/api/getJSON').then(res => {
                const data = res.data.carouselData.shelf;
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
            fetchItems(){  
            },
            setFilter(value) {
                this.filter = value;
                // console.log(this.filter)
                this.selectedItems = this.filterItems()
            },
            filterItems(){
                const items = this.items;
                return items.filter(item.type === this.filter);
            }
        },
        computed: {
            // selectedItems() {
            //     return this.filter === 'all' ? this.items : this.filterItems();
            // }
        }
  }
</script>
<style lang="scss">
   .task {
       background-color: #e5e5e5;
   }

</style>
