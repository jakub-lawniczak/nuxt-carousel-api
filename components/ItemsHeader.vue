<template>
    <div class="items-header">
        <h4 class="items-header__content text-center">Explore the whole collection</h4>
    </div>
</template>

<style lang="scss">
.items-header {  
    &__content {
        font-weight: $font-weight-bold;
        font-size: 28px;
        line-height: $leading-1_2;
        letter-spacing: $tracking--0_5;
        color: $ds-offblack-700;
        @include desktop-min {
            font-size: 32px;
        }
    }
}

</style>