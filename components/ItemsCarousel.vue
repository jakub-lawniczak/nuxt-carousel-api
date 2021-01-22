<template>
  <div class="items-carousel" :class="getCarouselClass">
    <ul class="items-carousel__list carousel" ref="flickity">
        <li 
            v-for="item in items" 
            class="items-carousel__list-item carousel-cell" 
            :key="item.img">
            <item :item="item" />
        </li>
    </ul>
  </div>
</template>
<script>
import Item from './Item.vue'
export default {
  components: {
    Item
  },
  props: {
    items: {
      type: Array,  
      default: () => []
    },
  },
  data() {
    return {
      flickity: null,
    }
  },
  computed: {   
    getCarouselClass() {
      return this.items.length > 4 ? 'element-full' : `element-${this.items.length}`;
    }  
  },
   watch: {
    items (val, oldVal) {  
      if(this.flickity) {
        this.flickity.destroy();   
      }
      //  Because flickity
      import('flickity').then(Flickity => {
        this.flickity = new Flickity.default(this.$refs.flickity, {groupCells: 1, pageDots: false, cellAlign: 'left',percentPosition: false, contain: true});
      });
    }
  },
  destroy() {
    this.flickity.destroy();
  },
}
</script>
<style lang="scss">
$defultPadding: 16px;

.carousel {
  max-width: 100%;
  overflow: hidden;
    &:focus {
    outline: 0 !important;
    border: 0;
  }
}
.flickity-viewport {
    @include desktop-min {
      padding-left: 48px;
    }
    @include desktop-air {
      padding-left: 92px;
    }
}
.flickity-slider {
  display: flex;
  justify-content: center !important;
}
.items-carousel {
  &.element-1,
  &.element-2,
  &.element-3,
  &.element-4 {
    margin: 0 auto;
    .flickity-viewport {
      padding-left: 0;
    }
    .flickity-button {
      display: none;
    }
    .items-carousel__list-item:last-of-type,
    .items-carousel__list-item:first-of-type {
      background-color: transparent;
      width: calc(161px + 16px);
    }
    .items-carousel__list-item:last-of-type {
      padding-right: 16px;
    }
    .items-carousel__list-item:first-of-type {
      padding-left: 16px;
    }
    @include tablet-min {
      .items-carousel__list-item:last-of-type,
      .items-carousel__list-item:first-of-type {
        width: auto;
        padding: 0 !important;
      }
    }
  }
  &.element-1 {
    width: 161px;
    @include tablet-min {
      width: 220px;
    }
  }
  &.element-2 {      
    @include tablet-min {
      width: calc((2*164px) + 24px);
    }
    @include desktop-min {
      width: calc((2*220px) + 24px);
    }
    @include desktop-air {
      width: calc((2*296px) + 24px);
    }
  }
  &.element-3 {
    @include tablet-min {
      width: calc((3*164px) + (2*16px));
    }
    @include desktop-min {
      width: calc((3*220px) + (2*24px));
    }
    @include desktop-air {
      width: calc((3*296px) + (2*24px));
    }
  }
  &.element-4 {
    @include tablet-min {
      width: calc((4*164px) + (3*16px));
    }
    @include desktop-min {
      width: calc((4*220px) + (3*24px));
    }
    @include desktop-air {
      width: calc((4*296px) + (3*24px));
    }
  }
  &.element-full {
    .items-carousel__list {
      .items-carousel__list-item:last-of-type {
        background-color: transparent;
        width: calc(161px + 16px);
        padding-right: 16px;
        @include tablet-min {
          width: calc(164px + (2*64px));
          padding-right: calc(2*64px);
        }
        @include desktop-min {
          width: calc(220px + (2*48px));
          padding-right: calc(2*48px);
        }
        @include desktop-air {
          width: calc(296px + (2*92px));
          padding-right: calc(2*92px);
        }
      }
      .items-carousel__list-item:first-of-type {
        background-color: transparent;
        width: calc(161px + 16px);
      }
      .items-carousel__list-item:first-of-type {
        padding-left: calc(16px);
      }
      @include tablet-min {
        .items-carousel__list-item:first-of-type {
          width: auto;
          padding: 0;
        }
      }
    }
  }
  &__list {
    position: relative;
    padding-left: 0;
    list-style: none; 
  }
}
.carousel-cell {
  width: 161px;
  height: 270px;
  margin-left: 16px;
  border-radius: 8px;
  &:first-child {
    margin-left: 0;
  }
  @include tablet-min {
    width: 164px;
    height: 273px;
  }
  @include desktop-min {
    width: 220px;
    height: 353px;
    margin-left: 24px;
  }
  @include desktop-air {
    width: 296px;
    height: 406px;
  }
}
.flickity-button {
  display: none;
  @include desktop-min {
    display: block;
    position: absolute;
    top: calc(50% - 20px);
    width: 40px;
    height: 40px;
    border: 1px solid $ds-grey-700;
    border-radius: 50%;
    background: $ds-white;
    cursor: pointer;
    &.previous {
      left: 28px;
    }
    &.next {
      right: 28px;
    }
  }
  @include desktop-air {
    &.previous {
      left: 72px;
    }
    &.next {
      right: 72px;
    }
  }
  &:disabled {
    display: none;
  }
}
.flickity-button-icon {
  width: 7.5px;
  height: 14px;
}
</style>

