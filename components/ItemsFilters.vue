<template>
    <div class="items-filters">
        <div class="row center-xs">
            <div class="items-filters__box row center-xs">
                <!-- <button v-for="(type, key) in types" class="items-filters__button button" @click="filter = type.filter" :class="{active : filter == type.filter}"> -->
                <button 
                    v-for="(type, key) in types" 
                    class="items-filters__button button" 
                    @click="selectFilter(key)"
                    :class="{active : selectedFilter === type.filter}">
                    {{type.name}}
                </button>
            </div>
        </div>
        <button class="items-filters__reset" v-show="selectedFilter !== 'all'" @click="resetFilter">
            <span class="icon">
                <svg width="8" height="8" viewBox="0 0 8 8" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M8 0.827735L4.83241 3.97752L8 7.12731L7.16759 7.95505L4 4.80526L0.832413 7.95505L0 7.12731L3.16759 3.97752L0 0.827735L0.832413 0L4 3.14979L7.16759 0L8 0.827735Z" fill="black"/>
                </svg>
            </span>
            <p class="text normal-12">Reset filter</p>


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
        margin: 32px 0;
        padding-bottom: 32px;
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
            // &:before,
            // &:after {
            //     position: absolute;
            //     // top: ;
            //     left: -8px;
            //     content: "";
            //     width: 8px;
            //     height: 1px;
            //     background: $ds-black;
            //     transition: all .3s;
            // }
            // &:before {
            //     transform:rotate(-45deg)
            // }
            // &:after {
            //     transform:rotate(45deg)
            // }
            // &:hover {
            //     &:before {
            //         transform:rotate(45deg)
            //     }
            //     &:after {
            //         transform:rotate(135deg)
            //     }
            // }
        }
    }

</style>