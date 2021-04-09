<template>
  <div class="container">
    <div>
      <h1 class="title">
        {{ title }}
      </h1>
      <ul>
        <li id="all" @click="filterDomen = ''">
          Все
        </li>
        <li id="lenta" @click="filterDomen = 'lenta'">
          Lenta.ru
        </li>
        <li id="mos" @click="filterDomen = 'mos'">
          Mos.ru
        </li>
      </ul>
      <label>
        <input
          v-model.trim="search"
          type="text"
          placeholder="Поиск по названию товара"
        >
      </label>
      <div @click="imgOn = true">Вкл</div>
      <div @click="imgOn = false">Откл</div>
      <div
        v-for=" post in displayedPosts"
        :key="displayedPosts.post"
      >
        <div>{{ post.title }}</div>
        <div>
          <img
            v-show="imgOn"
            :src="post.img"
            :alt="post.title"
          >
        </div>
        <div>{{ post.content }}</div>
        <div><a :href="post.link">Подробнее...</a></div>
      </div>
    </div>
    <nav aria-label="Page navigation example">
      <ul class="pagination">
        <li class="page-item">
          <button
            v-for="pageNumber in pages"
            type="button"
            class="page-link"
            @click="page = pageNumber"
          >
            {{ pageNumber }}
          </button>
        </li>
      </ul>
    </nav>
  </div>
</template>

<script>
export default {
  filters: {
  },
  data() {
    return {
      title: 'Список новостей',
      posts: [''],
      page: 1,
      perPage: 9,
      pages: [],
      search: '',
      filterDomen: '',
      imgOn: true,
    };
  },
  computed: {
    displayedPosts() {
      return this.paginate(this.displayFilter);
    },
    displayFilter() {
      return this.posts.filter((a) => {
        if (a) {
          const searchString = `${a.title} ${a.content}`;
          return (searchString.toLowerCase().indexOf(this.search.toLowerCase()) !== -1)
              && (a.link.indexOf(this.filterDomen) !== -1);
        } return false;
      });
    },
  },
  watch: {
    displayFilter() {
      this.setPages();
    },
    filterDomen() {
      this.setPages();
    },
  },
  created() {
    this.getPosts();
  },
  methods: {
    async getPosts() {
      const articles = await this.$axios.$get('https://inv01back.herokuapp.com/api/rss');
      this.posts = articles;
    },
    setPages() {
      const numberOfPages = Math.ceil(this.displayFilter.length / this.perPage);
      this.pages = [];
      for (let index = 1; index <= numberOfPages; index++) {
        this.pages.push(index);
      }
    },
    paginate(posts) {
      const { page } = this;
      const { perPage } = this;
      const from = (page * perPage) - perPage;
      const to = (page * perPage);
      return posts.slice(from, to);
    },
  },
};
</script>

<style>

</style>
