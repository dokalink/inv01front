<template>
  <div class="articles">
    <div
      v-for=" post in displayedPosts"
      :key="displayedPosts.post"
      class="articles__article article"
      :class="{ 'articles__article-imgon': imgOn }"
    >
      <c-article
        :post="post"
        :img-on="imgOn"
      />
    </div>
  </div>
</template>

<script>
export default {
  props: {
    imgOn: {
      type: Boolean,
      default: false,
    },
    displayedPosts: {
      type: Array,
      default: [],
    },
  },
};

</script>

<style lang="scss">
  @media screen and (max-width: 600px) {
    .article.articles__article{
      width: calc(1/1*100% - 20px);
    }
    .header .header__wrap {
      flex-direction: column;
    }
    .header .header__title {
      justify-content: space-between;
      width: 100%;
      margin-bottom: 10px;
    }
    .header .header__search {
      justify-content: space-between;
      width: 100%;
    }
    .article .article__header {
      flex-direction: column;
    }
    .article .article__content {
      -webkit-line-clamp: 3;
    }
    .article .article__imagebox {
      margin-right: 0px;
    }
    .article .article__image {
      width: 100%;
      height: auto;
    }
  }

  .articles {
    display: flex;
    flex-wrap:wrap;
    justify-content: flex-start;
    margin: 0 -10px;
    &__article {
      width: calc(1/2*100% - 20px);
      margin: 10px;
      }
    &__article-imgon {
      width: calc(100% - 20px);
    }
  }
</style>
