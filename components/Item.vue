<template>
  <div class="item">
      {{item.name}}
  </div>
</template>

<script>
export default {
    props: ['item']

}
</script>

<style lang="scss">
    .item {
        width: 161px;
        height: 270px;
        background-color: $ds-warning;
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

</style>