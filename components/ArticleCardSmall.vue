<template>
  <div class="card flex">
    <div class="flex flex-justify--space-between flex-align--center card__header">
      <div class="medium-brand">
        <img :src="faviconUrl" alt="" class="favicon" />
        <a :href="'https://' + mediumUrl" class="medium-name" target="_blank">{{ mediumName }}</a>
      </div>
      <span class="text--italic newshouse-text"
        >See this newshouse on the chart
        <img src="@/assets/svg/right-arrow.svg" width="10" style="vertical-align: inherit"
      /></span>
    </div>
    <div class="flex">
      <div class="image-ratio">
        <div :style="{ backgroundImage: `url(${imageUrl})` }" class="article-image"></div>
      </div>
      <div class="card__body">
        <div class="card__text-wrapper">
          <span class="card__title"> {{ title }} </span>/
        </div>
        <a :href="articleUrl" target="_blank">Read more</a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ArticleCardSmall',
  props: {
    imageUrl: {
      type: String,
      default: ''
    },
    title: {
      type: String,
      default: ''
    },
    content: {
      type: String,
      default: ''
    },
    sourceTitle: {
      type: String,
      default: 'NewsHouse'
    },
    articleUrl: {
      type: String,
      default: ''
    },
    faviconUrl: {
      type: String,
      default: ''
    },
    mediumName: {
      type: String,
      default: ''
    },
    mediumUrl: {
      type: String,
      default: ''
    }
  },
  computed: {
    setLogo() {
      return {
        /* LOGO */
      }
    }
  }
}
</script>

<style lang="scss" scoped>
.card {
  background: transparent;
  width: 100%;
  height: 55%;
  text-overflow: ellipsis;
  overflow: hidden;
  border-bottom: 1px solid black;
  border-right: none;
  border-left: none;
  border-radius: 0;

  .image-ratio {
    margin-bottom: 0.65rem;
    width: 60%;
    .article-image {
      height: 0;
      padding-top: 56.25%;
      background-position: center center;
      background-size: cover;
      position: relative;
    }
  }

  &:first-child {
    border-top: 1px solid black;
  }

  &--small {
    background: transparent;
    width: 100%;
    border: 1px solid black;
    border-radius: 0;
  }

  &__body {
    width: 90%;
    margin-left: 10px;
  }

  &__image {
    width: 100px;
    height: 80px;
  }

  &__header {
    width: 90%;
  }

  &__title {
    font-size: 1rem;
    font-weight: 700;
  }

  &__text {
    font-size: 0.8rem;
  }
}
.medium-brand {
  flex-shrink: 0;
  display: flex;
  align-items: center;
  margin-top: 5px;
  margin-bottom: 5px;
  .favicon {
    width: 1.1rem;
    height: 1.1rem;
  }
  .medium-name {
    margin-left: 0.5rem;
    color: #000;
    font-size: 1rem;
    font-style: italic;
    line-height: 1.25rem;
  }
}
</style>
