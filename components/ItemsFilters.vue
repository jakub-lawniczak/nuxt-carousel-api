<template>
    <div class="items-filters row center-xs">
        <div class="items-filters__box row center-xs">
            <!-- <button v-for="(type, key) in types" class="items-filters__button button" @click="filter = type.filter" :class="{active : filter == type.filter}"> -->
            <button 
                v-for="(type, key) in types" 
                class="items-filters__button button" 
                @click="selectedFilter(key)" 
                :class="{active : selectFilter == type.filter}">
                {{type.name}}
            </button>
        </div>
    </div>
</template>

<script> 
export default {
    data() {
        return {
            types: [
                {name: 'Type01 Plywood', filter: "Type01"},
                {name:'Type01 Venner', filter: "Type01 Veneer"},
                {name:'Type02', filter: "Type02"}
            ]
        }
    },
    methods: {
        selectedFilter(k) {
            // this.selectFilter = this.types[k].filter;
            this.$emit('filterWasSelected', this.types[k].filter)
            // return this.selectFilter;
        }
    },
      computed: {
    filterList() {
      return this.selectFilter;
    }
  }

}
</script>

<style lang="scss">
    .items-filters {
        margin-top: 32px !important;
        &__box {
            background-color: $ds-white;
            border-radius: 50px;
        }
        &__button {
            &.button {
                margin-right: 5px;
                padding: 8px;
                background-color: $ds-white;
                border: 0;
                font-size: 12px;
                font-weight: $font-weight-bold;
                color: $ds-offblack-600;
                &:last-child {
                    margin-right: 0;
                }
                &:hover {
                    background-color: $ds-orange;
                    border: 0;
                    color: $ds-white;
                }
                &.active {
                    background-color: $ds-orange;
                    color: $ds-white;
                    border: 0;
                }
            }
        }
    }

</style>