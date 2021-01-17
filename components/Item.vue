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
         @include tablet-min {
            background-image: url("~assets/images/welcome-hero_l.jpg");
            background-position: center center;
            justify-content: center;
        }

        @include desktop-min {
            background-image: url("~assets/images/welcome-hero_xl.jpg");
        }
    }

</style>