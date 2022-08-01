<template>
  <button class="bt-slider__button" :class="classes" role="button" ref="button" @click="$emit('click')">
    <i><</i>
  </button>
</template>

<script>
export default {
  name: "NavButton",
  data() {
    return {
      defaultClass: 'bt-slider__button',
    }
  },
  props: {
    size: String,
    isModuleDark: Boolean,
    isPrev: Boolean,
    isHidden: Boolean,
  },
  computed: {
    classes() {
      let classNames = '';
      this.isModuleDark ? classNames += '' : classNames += this.defaultClass + '--dark ';
      this.isPrev ? classNames += this.defaultClass + "--prev " : classNames += this.defaultClass + '--next ';
      classNames += this.defaultClass + "--" + this.size;
      return classNames;
    },

  },
  watch: {
    isHidden() {
      let activeClass = this.defaultClass + "--active";
      this.isHidden ? this.$refs.button.classList.remove(activeClass) : this.$refs.button.classList.add(activeClass);
    }
  }
}
</script>

<style lang="scss" scoped>
$screen-lg: 1200px;

.bt-slider{
  $self: &;

  &__button {
    background-color: #F6F6F6;
    color: #191919;
    border: none;
    border-radius: 50%;
    cursor: pointer;
    outline: none;

    &--prev {
      left: 3.2rem;
    }

    &--next {
      right: 3.2rem;
      i {
        transform: scaleX(-1);
      }
    }

    &--small {
      width: 3.2rem;
      height: 3.2rem;
    }

    &--big {
      position: absolute;
      top: 50%;
      width: 4.8rem;
      height: 4.8rem;
      opacity: 0;
      display: none;
      transform: translateX(0);
      transition-timing-function: ease-out;
      transition-duration: 0.3s;
      transition-property: opacity, transform;
    }

    &--dark {
      background-color: #191919;
      color: #FFFFFF;
    }

    @media screen and(min-width: $screen-lg) {
      #{$self}:focus-within {
        #{$self}__button--big {
          opacity: 1;
        }
      }

      &--small {
        display: none;
        opacity: 0;
      }

      &--big {
        display: flex;
        justify-content: center;
        align-items: center;
        opacity: 0;
      }

      &--active {
        opacity: 1;

        &#{$self}__button--prev {
          transform: translateX(3.2rem);
        }
        &#{$self}__button--next {
          transform: translateX(-3.2rem);
        }
      }
    }
  }
}

</style>
