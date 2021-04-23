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
  .articles {
    display: flex;
    flex-wrap:wrap;
    justify-content: flex-start;
    margin: 0 -10px;
    &__article {
      width: calc(1/2*100% - 20px);
      margin: 10px;
      &-imgon {
        width: calc(1/1*100% - 20px);
      }
    }
  }
</style>
