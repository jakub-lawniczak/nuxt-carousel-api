<template>
  <a :href="'/' + item.link" class="item">
      <div class="item__img-hld">
        <!-- Overlay option  -->
        <!-- <div class="item__img-overlay"></div>  -->
        <div class="item__img" :style="{ backgroundImage: `url(${imgUrl})`}"></div>
      </div>
      <div class="item__data">
        <div class="item__edit-icon">
            <svg class="icon" width="14" height="14" viewBox="0 0 14 14" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path fill-rule="evenodd" clip-rule="evenodd" d="M6.41682 4.21384C5.60116 4.21384 4.91583 3.62171 4.7218 2.82045H0V1.8929H4.72192C4.91612 1.09189 5.60133 0.5 6.41682 0.5C7.2323 0.5 7.91751 1.09189 8.11171 1.8929H13.999V2.82045H8.11183C7.9178 3.62171 7.23247 4.21384 6.41682 4.21384ZM6.41682 3.28613C6.90006 3.28613 7.2918 2.87042 7.2918 2.35762C7.2918 1.84481 6.90006 1.4291 6.41682 1.4291C5.93357 1.4291 5.54183 1.84481 5.54183 2.35762C5.54183 2.87042 5.93357 3.28613 6.41682 3.28613Z" fill="white"/>
                <path d="M3.55503 11.1791H0V12.1054H3.55462C3.74767 12.9048 4.42968 13.4964 5.24246 13.5L5.24993 13.5L5.2574 13.5C6.07019 13.4964 6.7522 12.9048 6.94525 12.1054H14V11.1791H6.94484C6.75065 10.378 6.06544 9.78614 5.24994 9.78614C4.43444 9.78614 3.74922 10.378 3.55503 11.1791Z" fill="white"/>
                <path d="M9.33299 8.85706C8.51731 8.85706 7.83197 8.26485 7.63796 7.46351H0V6.53607H7.63807C7.83224 5.73496 8.51747 5.14299 9.33299 5.14299C10.1485 5.14299 10.8337 5.73496 11.0279 6.53607H13.9993V7.46351H11.028C10.834 8.26485 10.1487 8.85706 9.33299 8.85706Z" fill="white"/>
            </svg>
        </div> 
        <h4 class="item__name">{{ item.name }}</h4>
        <p class="item__type">{{ item.type }}</p>
        <p class="item__size-info">Width: {{ item.width }} cm</p>
        <p class="item__size-info">Height: {{ item.height }} cm</p>
        <p class="item__size-info">Depth: {{ item.depth }} cm</p>
      </div>
  </a>
</template>

<script>
export default {
    props: ['item'],
    data() {
        return {
            isIE11: !!window.MSInputMethodContext && !!document.documentMode,
        }
    },
    computed: {
        imgUrl() {
            if(this.isIE11) {
                return require(`~/assets/images/${this.item.img.replace(/^assets\/images\//, '')}`);
            } else {
                return require(`~/assets/images/${this.item.img_webp.replace(/^assets\/images\//, '')}`);
            }
        },
    },
}
</script>

<style lang="scss">
    .item {
        position: relative;
        display: block;
        border-radius: 12px;
        background-color: $ds-white;
        color: $ds-offblack-600;
        &__img-hld {
            position: relative;
            width: 161px;
            height: 161px;
            @include tablet-min {
                width: 164px;
                height: 164px;
            }
            @include desktop-min {
                width: 220px;
                height: 220px;
            }
            @include desktop-air {
                width: 296px;
                height: 270px;
            }   
        } 
        &__img {
            height: 100%;
            width: 100%;
            background-size: cover;
            background-repeat: no-repeat;
            border-radius: 12px 12px 0px 0px;
        }
        &__img-overlay {
            position: absolute;
            top: 0;
            right: 0;
            bottom: 0;
            left: 0;
            border-radius: 12px 12px 0px 0px;
            background: rgb(199,200,203);
            opacity: .4;
            background: linear-gradient(96deg, $c-overlay-first 9.71%, $c-overlay-second 50.84%);
            transition: all .3s;
        }
        &__data {
            position: relative;
            padding: 13px 16px 12px 16px;
        }
        &__name {
            font-size: 14px;
            font-weight: $font-weight-bold;
            color: $ds-offblack-700;
            line-height: $leading-1_4;
            &:first-letter {
                text-transform: uppercase;
            }
        }
        &__type {
            font-size: 12px;
            line-height: $leading-1_4;
            @include desktop-min {
                font-size: 14px;
            }
        }
        &__size-info {
            font-size: 10px;
            line-height: $leading-1_4;
            @include desktop-min {
                font-size: 12px;
            }
        }
        &__edit-icon {
            position: absolute;
            top: -18px;
            right: 8px;
            z-index: 2;
            display: flex;
            justify-content: center;
            align-items: center;
            width: 36px;
            height: 36px;
            border: 1px solid transparent;
            border-radius: 50%;
            background-color: $ds-orange;
            transition: all .3s;
            .icon {
                display: block;
                transition: all .3s;
            }
            @include tablet-min {
                right: 6px;
            }
            @include desktop-min {
                right: 16px;
            }
        }
        &:hover{ 
            .item__img-overlay {
                opacity: 0;
            }
            .item__edit-icon {
                background-color: $ds-white;
                border: 1px solid $ds-orange;
            .icon {
                transform: rotateY(180deg);
                    path {
                        fill: $ds-orange;
                    }
                    // I  TRIED SOMETHING NEW BUT... SORRY, I AM NOT A GRAPHIC
                    // path {
                    //     fill: $ds-white; 
                    //     transition: 0.5s;
                    //     -webkit-transition: 0.5s;
                    //     &:nth-child(1) {
                    //         transform: translate(4.8px, 0); 
                    //     }
                    //     &:nth-child(2) {
                    //         transform: translate(-6.6px, 0);
                    //     }
                    //     &:nth-child(3) {
                    //         transform: translate(6px, 0); 
                    //     }       
                    // }
                }
            }
        }
    }


</style>