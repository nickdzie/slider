<template>
  <div class="bt-fl-slider__pagination">
    <nav-button :is-prev="true" :is-dark="false" size="small" @click="$emit('click-prev')"></nav-button >
    <div class="bt-fl-slider__pagination__text">
        <span class="bt-fl-slider__pagination--current">
          {{currentPage}}
        </span>
      <span class="bt-fl-slider__pagination--separator">
          von
        </span>
      <span class="bt-fl-slider__pagination--pages">
          {{pages}}
        </span>
    </div>
    <nav-button :is-prev="false" :is-dark="false" size="small" @click="$emit('click-next')"></nav-button >
  </div>
</template>

<script>
import NavButton from "@/components/NavButton";
export default {
  name: "Pagination",
  components: {NavButton},
  props: {
    currentPage: Number,
    pages: Number,
  },
}
</script>

<style lang="scss" scoped>
$black: #191919;
$white: #FFFFFF;
$screen-lg: 1200px;

.bt-fl-slider {

  &__pagination {
    height: 3.2rem;
    margin-bottom: 4.8rem;
    display: flex;
    justify-content: space-between;
    align-items: center;

    &__text {
      margin: 0 3.2rem;
    }

    @media screen and(min-width: $screen-lg) {
      justify-content: center;

      &__text {
        margin: 0;
      }
    }
  }
}
</style>
