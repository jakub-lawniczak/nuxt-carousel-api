
<template>
    <section class="task">
        <div class="container-cstm-fluid">
            <items-header />
            <items-filters selectFilter="all"/>
            <items-carousel selectFilter="all" @filterWasSelected="filter = $event"/>
        </div>   
    </section>
</template>

<script>
import ItemsHeader from '../components/ItemsHeader.vue'
import ItemsFilters from '../components/ItemsFilters.vue'
import ItemsCarousel from '../components/ItemsCarousel.vue'
    export default {
        components: { ItemsCarousel, ItemsHeader, ItemsFilters },
        data() {
            return {
                filter: 'all'
            }
        }
  
  }
</script>
<style lang="scss">
   .task {
       background-color: #e5e5e5;
   }

</style>
