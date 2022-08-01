<template>
  <main>
    <section class="bt-module-row bt-module-slider">
      <header>
        <h2>
          Headline
        </h2>
      </header>
      <FlSlider :slides-per-group-xs="1" :slides-per-column-xs="1" :slides-per-group-sm="2" :slides-per-column-sm="1" :slides-per-group-md="4" :slides-per-column-md="2" :slides-per-group-lg="8" :slides-per-column-lg="2" :results="50">
        <template v-slot:items>
          <div class="bt-fl-slider__item"><a href="#">1</a></div>
          <div class="bt-fl-slider__item"><a href="#">2</a></div>
          <div class="bt-fl-slider__item"><a href="#">3</a></div>
          <div class="bt-fl-slider__item"><a href="#">4</a></div>
          <div class="bt-fl-slider__item"><a href="#">5</a></div>
          <div class="bt-fl-slider__item"><a href="#">6</a></div>
          <div class="bt-fl-slider__item"><a href="#">7</a></div>
          <div class="bt-fl-slider__item"><a href="#">8</a></div>
          <div class="bt-fl-slider__item"><a href="#">9</a></div>
          <div class="bt-fl-slider__item"><a href="#">10</a></div>
          <div class="bt-fl-slider__item"><a href="#">11</a></div>
          <div class="bt-fl-slider__item"><a href="#">12</a></div>
          <div class="bt-fl-slider__item"><a href="#">13</a></div>
          <div class="bt-fl-slider__item"><a href="#">14</a></div>
          <div class="bt-fl-slider__item"><a href="#">15</a></div>
          <div class="bt-fl-slider__item"><a href="#">16</a></div>
          <div class="bt-fl-slider__item"><a href="#">17</a></div>
          <div class="bt-fl-slider__item"><a href="#">18</a></div>
          <div class="bt-fl-slider__item"><a href="#">19</a></div>
          <div class="bt-fl-slider__item"><a href="#">20</a></div>
        </template>
      </FlSlider>
    </section>
    <section class="bt-module-row bt-module-slider">
      <header>
        <h2>
          Headline
        </h2>
      </header>
      <FlSlider :slides-per-group-xs="1" :slides-per-column-xs="1" :slides-per-group-sm="2" :slides-per-column-sm="1" :slides-per-group-md="4" :slides-per-column-md="2" :slides-per-group-lg="8" :slides-per-column-lg="2" :results="50">
        <template v-slot:items>
          <div class="bt-fl-slider__item"><a href="#">1</a></div>
          <div class="bt-fl-slider__item"><a href="#">2</a></div>
          <div class="bt-fl-slider__item"><a href="#">3</a></div>
          <div class="bt-fl-slider__item"><a href="#">4</a></div>
          <div class="bt-fl-slider__item"><a href="#">5</a></div>
          <div class="bt-fl-slider__item"><a href="#">6</a></div>
          <div class="bt-fl-slider__item"><a href="#">7</a></div>
          <div class="bt-fl-slider__item"><a href="#">8</a></div>
          <div class="bt-fl-slider__item"><a href="#">9</a></div>
          <div class="bt-fl-slider__item"><a href="#">10</a></div>
          <div class="bt-fl-slider__item"><a href="#">11</a></div>
          <div class="bt-fl-slider__item"><a href="#">12</a></div>
          <div class="bt-fl-slider__item"><a href="#">13</a></div>
          <div class="bt-fl-slider__item"><a href="#">14</a></div>
          <div class="bt-fl-slider__item"><a href="#">15</a></div>
          <div class="bt-fl-slider__item"><a href="#">16</a></div>
          <div class="bt-fl-slider__item"><a href="#">17</a></div>
          <div class="bt-fl-slider__item"><a href="#">18</a></div>
          <div class="bt-fl-slider__item"><a href="#">19</a></div>
          <div class="bt-fl-slider__item"><a href="#">20</a></div>
        </template>
      </FlSlider>
    </section>
    <section class="bt-module-row bt-module-slider">
      <header>
        <h2>
          Headline
        </h2>
      </header>
      <FlSlider :slides-per-group-xs="1" :slides-per-column-xs="1" :slides-per-group-sm="2" :slides-per-column-sm="1" :slides-per-group-md="4" :slides-per-column-md="2" :slides-per-group-lg="8" :slides-per-column-lg="2" :results="50">
        <template v-slot:items>
          <div class="bt-fl-slider__item"><a href="#">1</a></div>
          <div class="bt-fl-slider__item"><a href="#">2</a></div>
          <div class="bt-fl-slider__item"><a href="#">3</a></div>
          <div class="bt-fl-slider__item"><a href="#">4</a></div>
          <div class="bt-fl-slider__item"><a href="#">5</a></div>
          <div class="bt-fl-slider__item"><a href="#">6</a></div>
          <div class="bt-fl-slider__item"><a href="#">7</a></div>
          <div class="bt-fl-slider__item"><a href="#">8</a></div>
          <div class="bt-fl-slider__item"><a href="#">9</a></div>
          <div class="bt-fl-slider__item"><a href="#">10</a></div>
          <div class="bt-fl-slider__item"><a href="#">11</a></div>
          <div class="bt-fl-slider__item"><a href="#">12</a></div>
          <div class="bt-fl-slider__item"><a href="#">13</a></div>
          <div class="bt-fl-slider__item"><a href="#">14</a></div>
          <div class="bt-fl-slider__item"><a href="#">15</a></div>
          <div class="bt-fl-slider__item"><a href="#">16</a></div>
          <div class="bt-fl-slider__item"><a href="#">17</a></div>
          <div class="bt-fl-slider__item"><a href="#">18</a></div>
          <div class="bt-fl-slider__item"><a href="#">19</a></div>
          <div class="bt-fl-slider__item"><a href="#">20</a></div>
        </template>
      </FlSlider>
    </section>
  </main>
</template>

<script>
import FlSlider from "./components/FlSlider";

export default {
  name: 'app',
  components: {
    FlSlider,
  }
}
</script>

<style lang="scss">
:root {
  --font-sans: 'Noto Sans Display', Arial,Helv,Helvetica,Verdana,sans-serif;
  --font-serif: 'Noto Serif',Georgia,Times New Roman,Times,serif;
  font-size: 10px;
}
body {
  height: 100vh;
  width: 100vw;
  margin: 0;
  padding: 0;
}
main {
  $screen-xs: 480px;
  $screen-sm: 768px;
  $screen-md: 992px;
  $screen-lg: 1200px;
  $black: #191919;
  $white: #FFFFFF;
  padding: 0 1.6rem;

  @media screen and(min-width: $screen-sm){
    padding: 0 3.2rem;
  }
  @media screen and(min-width: $screen-md){
    padding: 0 3.6rem;
  }
  @media screen and(min-width: $screen-lg){
    padding: 0 4.4rem;
  }
}
</style>
