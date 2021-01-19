<template>
  <div class="items-carousel" :class="demandOnelementsNumber()">
    <ul class="items-carousel__list carousel" ref="flickity">
        <li v-for="item in items" class="items-carousel__list-item carousel-cell">
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
    carouselElements: '',
    classDemandOnElements: '',
    }
  },
  methods: {
    demandOnelementsNumber() {
      if(this.carouselElements == 1) {
        return 'element-1';
      } else if (this.carouselElements == 2){ 
        return 'element-2';
      } else if (this.carouselElements == 3){ 
        return 'element-3';
      } else if (this.carouselElements == 4){ 
        return 'element-4';
      }
    },        

  },
   watch: {
      items (val, oldVal) {
        if (val !== oldVal) {
          console.log(this.items.length)
          this.carouselElements = this.items.length;
          console.log(this.carouselElements);
          }
      }
    },
  mounted() {   
    import('flickity').then(Flickity => {
      console.log(Flickity);
      this.flickity = new Flickity.default(this.$refs.flickity, {groupCells: 4, pageDots: false, cellAlign: 'left',percentPosition: false});
    });

  },
  computed: {
  },
  destroy() {
    this.flickity.destroy();
  },
}
</script>
 
<style lang="scss">
.carousel {
  max-width: 100%;
  overflow: hidden;
    &:focus {
    outline: 0 !important;
    border: 0;
  }
}
.flickity-viewport {
    padding-left: 16px;
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
  }
  &.element-1 {
    width: 161px;
    @include tablet-min {
      width: 220px;
    }
  }
  &.element-2 {
    @include tablet-min {
      width: calc((2*164px) + 16px);
    }
    @include desktop-min {
      width: calc((2*220px) + 16px);
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
      width: calc((3*220px) + (2*16px));
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
      width: calc((4*220px) + (3*16px));
    }
    @include desktop-air {
      width: calc((4*296px) + (3*24px));
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
  background-color: $ds-white;
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
  }
  @include desktop-air {
      width: 296px;
      height: 406px;
  }
}
.flickity-button {
    display: none;
    width: 40px;
    height: 40px;
    border: 1px solid $ds-grey-700;
    border-radius: 50%;
    background: $ds-white;
    @include desktop-min {
      display: block;
      position: absolute;
      top: 50%;
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

