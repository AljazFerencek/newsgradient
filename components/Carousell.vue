<template>
  <div class="carousel__container flex flex-justify--center flex-align--center">
    <div v-if="this.$store.state.carousel.selectedSlant !== 1" class="carousel__subitem carousel__item--left">
      <CarousellItem
        :articles="getArticles(this.$store.state.carousel.selectedSlant - 1)"
        class="carousel-item-selector"
      />
    </div>
    <div @click="decrement" class="carousel__arrow">
      <img src="@/assets/svg/carousel/left-arrow.svg" />
    </div>
    <div class="carousel__item">
      <CarousellItem :articles="getArticles(this.$store.state.carousel.selectedSlant)" class="carousel-item-selector" />
    </div>
    <div @click="increment" class="carousel__arrow">
      <img src="@/assets/svg/carousel/right-arrow.svg" />
    </div>
    <div v-if="this.$store.state.carousel.selectedSlant !== 5" class="carousel__subitem carousel__item--right">
      <CarousellItem
        :articles="getArticles(this.$store.state.carousel.selectedSlant + 1)"
        class="carousel-item-selector-item"
      />
    </div>
  </div>
</template>

<script>
import CarousellItem from './CarousellItem'

export default {
  name: 'Carousell',
  components: { CarousellItem },
  computed: {
    calculateMainHeight() {
      const carouselItems = document.getElementsByClassName('carousel-item-selector')
      let height = 0
      Array.from(carouselItems).forEach((elem) => {
        const box = elem.getBoundingClientRect()
        console.log(box.height)
        if (box.height > height) {
          height = box.height
        }
      })
      return height
    }
  },
  methods: {
    decrement() {
      this.$store.commit('carousel/DECREMENT_ITEM')
    },
    increment() {
      this.$store.commit('carousel/INCREMENT_ITEM')
    },
    getArticles(slant) {
      if (slant - 1 < 1 || slant + 1 > 5) {
        return []
      }
      return this.$store.state.events.articles[slant]
    }
  }
}
</script>

<style scoped lang="scss">
.carousel {
  &__container {
    position: relative;
    overflow: hidden;
    margin-bottom: 15vh;
  }

  &__subitem {
    width: 65vw;
    position: absolute;
    opacity: 0.3;
    top: 0;
  }

  &__item {
    width: 65vw;

    &--left {
      left: -55vw;
      overflow-y: hidden;
    }

    &--right {
      right: -55vw;
      overflow-y: hidden;
    }
  }

  &__arrow {
    width: 3vw;
    cursor: pointer;
    margin: 10px;

    img {
      position: fixed;
      top: 45%;
      width: 3vw;
    }
  }
}
</style>
