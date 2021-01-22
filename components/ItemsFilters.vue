<template>
    <div class="items-filters mb-32 pb-32">
        <div class="row center-xs">
            <div class="items-filters__box row between-xs bg-white">
                <button 
                    v-for="(type, key) in types" 
                    class="items-filters__button button bold-12 sm:bold-14 text-offblack-600 text-center bg-white p-0"
                    @click="selectFilter(key)"
                    :class="{active : selectedFilter === type.filter}"
                    :key="type.name">
                    {{type.name}}
                </button>
            </div>
        </div>
        <button class="items-filters__reset blod-12 sm:blod-14" v-show="selectedFilter !== 'all'" @click="resetFilter">
            <span class="icon">
                <svg width="8" height="8" viewBox="0 0 8 8" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M8 0.827735L4.83241 3.97752L8 7.12731L7.16759 7.95505L4 4.80526L0.832413 7.95505L0 7.12731L3.16759 3.97752L0 0.827735L0.832413 0L4 3.14979L7.16759 0L8 0.827735Z" fill="black"/>
                </svg>
            </span>
            <p class="text normal-14">Reset filter</p>
        </button>
    </div>
</template>

<script> 
export default {
    data() {
        return {
            types: [
                {name: 'Type01 Plywood', filter: "1"}, 
                {name:'Type01 Venner', filter: "1v"},
                {name:'Type02', filter: "2"}
            ],
            selectedFilter: 'all', 
        }
    },
    methods: {
        selectFilter(key) {
            this.selectedFilter = this.types[key].filter;
            this.$emit('filterWasSelected', this.selectedFilter)
        },
        resetFilter() {
            this.selectedFilter = 'all';
            this.$emit('filterWasSelected', this.selectedFilter)
        }
    },
}
</script>

<style lang="scss">
    .items-filters {
        position: relative;
        &__box {
            border-radius: 50px;
            width: 288px;
            @include mobile-middle {
                width: 459px;
            }
            @include tablet-min {
                width: 519px;
            }
        }
        &__button {
            &.button {
                display: flex;
                justify-content: center;
                height: 40px;
                width: 37%;
                border: 0;
                border-radius: 50px;
                font-size: 12px; // additional
                font-weight: $font-weight-bold; //additional
                @include tablet-min {
                    width: 36%
                }
                &:last-child { 
                    width: 26%;
                    margin-right: 0;
                    @include tablet-min {
                        width: 28%;
                    }
                }
                &:hover,
                &.active {
                    background-color: $ds-orange;
                    border: 0;
                    color: $ds-offwhite-600;
                }
                @include mobile-middle  {
                    font-size: 14px;
                }
            }
        }
        &__reset {
            position: absolute;
            left: 50%;
            bottom: 0;
            display: flex;
            align-content: center;
            // margin: 16px auto 28px;
            background: transparent;
            border: 0;
            transform: translateX(-50%);
            .text {
                color: $ds-offblack-600;
            }
            .icon {
                display: block;
                margin-right: 8px;
                transition: all .3s
            }
            &:hover {
                .icon {
                    transform: rotate(90deg);
                }
            }
        }
    }

</style>