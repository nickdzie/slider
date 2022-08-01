<template>
  <div class="bt-fl-slider" @mouseenter="hideButtons = false" @mouseleave="hideButtons = true">
    <div class="bt-fl-slider__wrapper" ref="wrapper">
      <nav-button :is-prev="true" :is-module-dark="false" :size="'big'" :is-hidden="hideButtons" @click="prevSlide"></nav-button >
      <div class="bt-fl-slider__wrapper__track" ref="track">
        <slot name="items"></slot>
      </div>
      <nav-button :is-prev="false" :is-module-dark="false" :size="'big'" :is-hidden="hideButtons" @click="nextSlide"></nav-button>
    </div>
    <pagination :current-page="currentPage" :pages="pages" @click-prev="prevSlide" @click-next="nextSlide"></pagination>
  </div>
</template>

<script>
import $ from 'jquery'
import Pagination from "@/components/Pagination";
import NavButton from "@/components/NavButton";
export default {
  name: "FlSlider",
  components: {NavButton, Pagination},
  props: {
    slidesPerColumnXs: Number,
    slidesPerGroupXs: Number,
    slidesPerColumnSm: Number,
    slidesPerGroupSm: Number,
    slidesPerColumnMd: Number,
    slidesPerGroupMd: Number,
    slidesPerColumnLg: Number,
    slidesPerGroupLg: Number,
    results: Number
  },
  data() {
    return {
      pages: 0,
      currentPage: 1,
      slideWidth: null,
      currentViewport: null,
      currentSlidesPerGroup: null,
      currentSlidesPerColumn: null,
      slides: [],
      slideGroups: [],
      isSlidesWrapped: null,
      hideButtons: true,
    }
  },
  mounted() {
    window.addEventListener("resize", this.setViewport);
    this.$refs.track.addEventListener("scroll", this.handleScroll);
    this.slides = this.$refs.track.childNodes;
    this.slideWidth = this.$refs.track.firstElementChild.getBoundingClientRect().width;
    this.calcPages();
    this.setViewport();
  },
  watch: {
    currentViewport() {
      this.handleViewportChange();
    }
  },
  methods: {
    calcPages() {
      this.pages = Math.ceil(this.results / this.currentSlidesPerGroup);
    },
    setViewportInfo() {
      switch (this.currentViewport) {
        case 'LG':
          this.currentSlidesPerColumn = this.slidesPerColumnLg;
          this.currentSlidesPerGroup = this.slidesPerGroupLg;
          break;
        case 'MD':
          this.currentSlidesPerColumn = this.slidesPerColumnMd;
          this.currentSlidesPerGroup = this.slidesPerGroupMd;
          break;
        case 'SM':
          this.currentSlidesPerColumn = this.slidesPerColumnSm;
          this.currentSlidesPerGroup = this.slidesPerGroupSm;
          break;
        default:
          this.currentSlidesPerColumn = this.slidesPerColumnXs;
          this.currentSlidesPerGroup = this.slidesPerGroupXs;
          break;
      }
    },
    wrapSlides() {
      let children = $(".bt-fl-slider__wrapper__track .bt-fl-slider__item");
      const itemsToWrap = 6;
      for(let i = 0; i <= children.length; i += itemsToWrap) {
        let $wrapperDiv = $("<div/>", { class: "bt-fl-slider__item-group"});
        if(i === itemsToWrap) $wrapperDiv = $("<div/>", { class: "bt-fl-slider__item-group bt-fl-slider__item-group--next"});
        $(children).slice(i, i + 6).wrapAll($wrapperDiv);
      }
    },
    unwrapSlides() {
      let wrapper = $(".bt-fl-slider__item");
      wrapper.unwrap();
    },
    handleScroll() {
      let page = this.currentPage;
      for(let [index, item] of this.slides.entries()) {
        let itemOffset = item.getBoundingClientRect().left;
        if(itemOffset > 0) {
          page = index + 1;
          break;
        }
      }
      page = Math.ceil(page / this.currentSlidesPerGroup);
      return this.currentPage = page;
    },
    setViewport() {
      let viewport = window.innerWidth;
      if(viewport < 768) return this.currentViewport = 'XS';
      if(viewport < 992) return this.currentViewport = 'SM';
      if(viewport < 1200) return this.currentViewport = 'MD';
      return this.currentViewport = 'LG'
    },
    handleViewportChange() {
      this.setViewportInfo();
      this.calcPages();
      this.checkSlides(this.isSlidesWrapped);
    },
    prevSlide() {
      let currentScroll = this.$refs.track.scrollLeft;
      let amountToSlide = this.slideWidth * (this.currentSlidesPerGroup / this.currentSlidesPerColumn);
      this.$refs.track.scrollTo({left: currentScroll - amountToSlide, behavior: "smooth"});
    },
    nextSlide() {
      let currentScroll = this.$refs.track.scrollLeft;
      let amountToSlide = this.slideWidth * (this.currentSlidesPerGroup / this.currentSlidesPerColumn);
      this.$refs.track.scrollTo({left: currentScroll + amountToSlide, behavior: "smooth"});
    },
    changeViewport() {
      return this.currentViewport = 'LG';
    },
    checkSlides(isWrapped) {
      if(this.currentViewport === 'LG' && !isWrapped) {
        this.wrapSlides();
        this.isSlidesWrapped = true;
        return;
      }
      if(this.currentViewport !== 'LG' && isWrapped) {
        this.unwrapSlides();
        this.isSlidesWrapped = false;
      }
    }
  },
}
</script>

<style lang="scss">
$screen-xs: 480px;
$screen-sm: 768px;
$screen-md: 992px;
$screen-lg: 1200px;
$black: #191919;
$white: #FFFFFF;
.bt-fl-slider {

  &__item {
    width: 24.2rem;
    height: 35.2rem;
    border-radius: 0.8rem;
    flex-shrink: 0;
    overflow: hidden;
    background-color: #191919;
    scroll-snap-align: start;
  }

  &__wrapper {
    margin: {
      left: calc(-50vw + 50%);
      right: calc(-50vw + 50%);
      bottom: 3.2rem;
    }
    position: relative;
    overflow: hidden;

    &__track {
      padding: 0 1.6rem;
      display: grid;
      grid-auto-flow: column;
      gap: 1.6rem;
      scroll-snap-type: x proximity;
      scroll-padding-inline: 1.6rem;
      overflow: auto;
    }
  }

  @media screen and(min-width: $screen-md) {
    &__wrapper {
      &__track {
        grid-template-rows: 1fr 1fr;
      }
    }
  }

  @media screen and(min-width: $screen-lg) {
    &__wrapper {
      padding: {
        left: calc(50vw - 600px);
        right: calc(50vw - 600px);
      };

      &__track {
        display: flex;
        flex-wrap: nowrap;
        flex-direction: row;
        overflow: hidden;
      }
    }

    &__item-group {
      margin-right: 100vw;
      display: grid;
      gap: 1.6rem;
      grid-auto-flow: column;
      grid-template-rows: 1fr 1fr;
      scroll-snap-align: center;
      scroll-padding-inline: 100vw;
    }

    &__item {
      transition: margin-right 0.6s ease-in-out;
      margin-right: 1.6rem;
    }
  }
}
</style>
