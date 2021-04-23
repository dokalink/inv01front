<template>
  <nav class="pagination">
    <div
      v-if="page > 3"
      class="pagination__item"
      @click="page = 1"
    >
      1 ...
    </div>

    <div
      v-for="pageNumber in pages.slice(pageStart(page,pages.length), pageEnd(page,pages.length))"
      class="pagination__item"
      @click="page = pageNumber"
    >
      {{ pageNumber }}
    </div>

    <div
      v-if="page < (pages.length - 2)"
      class="pagination__item"
      @click="page = pages.length"
    >
      ... {{ pages.length }}
    </div>
  </nav>
</template>

<script>
export default {
  props: {
    pages: {
      type: Array,
      default: [],
    },
    page: {
      type: Number,
      default: 1,
    },
  },
  methods: {
    pageStart(carentPage, maxPages) {
      if (carentPage < 4) {
        return 0;
      }
      if (carentPage > (maxPages - 3)) {
        return maxPages - 5;
      }
      return carentPage - 3;
    },
    pageEnd(carentPage, maxPages) {
      if (carentPage < 3) {
        return 5;
      }
      if (carentPage > (maxPages - 2)) {
        return maxPages;
      }
      return carentPage + 2;
    },
  }
};
</script>

<style lang="scss">
  .pagination {
    display: flex;
    justify-content: center;
    font-size: 18px;
    font-weight: bold;
    cursor: pointer;
    padding: 50px 0 20px;
    &__item {
      padding: 10px;
    }

  }
</style>
