<template>
  <div class="container">
    <header class="header">
      <div class="header__wrap">
        <div class="header__title">
          <h1>{{ title }}</h1>
          <div class="header__update">
            <svg
              width="20"
              height="20"
              viewBox="0 0 20 16"
              fill="none"
              xmlns="http://www.w3.org/2000/svg"
            >
              <path
                d="M9.29973 0.0524773C10.3583 -0.0731896 11.3802 0.0315329 12.3247 0.316378C15.4638 1.26307 17.7722 4.233 17.8129 7.75586H19.8649C19.9789 7.75586 20.04 7.90247 19.9708 7.99882L16.8684 12.3427C16.8155 12.4139 16.7096 12.4139 16.6607 12.3427L13.5584 8.00301C13.4892 7.90247 13.5502 7.76005 13.6642 7.76005H15.7121C15.6755 5.44359 14.2871 3.46643 12.3247 2.61608C11.5838 2.29354 10.7654 2.13017 9.90636 2.17625C8.72566 2.23908 7.63861 2.69567 6.7592 3.41616C6.29099 3.80154 5.607 3.70939 5.25279 3.21091C4.91487 2.73756 5.00851 2.07572 5.45636 1.71128C6.53934 0.819046 7.85846 0.224222 9.29973 0.0524773ZM13.2408 12.594C12.3655 13.3187 11.2743 13.7753 10.0936 13.834C9.23051 13.88 8.41217 13.7125 7.67525 13.3941C5.71285 12.5438 4.32045 10.5666 4.28788 8.25015H6.33577C6.44977 8.25015 6.51084 8.10354 6.44163 8.0072L3.33925 3.66331C3.28632 3.5921 3.18047 3.5921 3.13161 3.66331L0.0292317 8.00301C-0.0399815 8.10354 0.0210892 8.24596 0.135087 8.24596H2.18705C2.2237 11.7688 4.53216 14.7429 7.67525 15.6854C8.61981 15.9703 9.64172 16.0708 10.7003 15.9493C12.1415 15.7818 13.4607 15.187 14.5436 14.2947C14.9915 13.9261 15.0851 13.2685 14.7472 12.7951C14.393 12.3008 13.709 12.2087 13.2408 12.594Z"
                fill="#0029FF"
              />
            </svg>
          </div>
        </div>

        <div class="header__search">
          <input
            v-model.trim="search"
            type="text"
            placeholder="Поиск по названию товара"
          >
          <svg
            width="20"
            height="20"
            viewBox="0 0 20 20"
            fill="none"
            xmlns="http://www.w3.org/2000/svg"
          >
            <path
              fill-rule="evenodd"
              clip-rule="evenodd"
              d="M8.48485 1.81818C4.80295 1.81818 1.81818 4.80295 1.81818 8.48485C1.81818 12.1667 4.80295 15.1515 8.48485 15.1515C10.2942 15.1515 11.9352 14.4307 13.1363 13.2606C13.1548 13.2382 13.1745 13.2165 13.1955 13.1956C13.2165 13.1746 13.2382 13.1549 13.2606 13.1364C14.4307 11.9352 15.1515 10.2942 15.1515 8.48485C15.1515 4.80295 12.1667 1.81818 8.48485 1.81818ZM15.093 13.8074C16.2669 12.3518 16.9697 10.5004 16.9697 8.48485C16.9697 3.7988 13.1709 0 8.48485 0C3.7988 0 0 3.7988 0 8.48485C0 13.1709 3.7988 16.9697 8.48485 16.9697C10.5004 16.9697 12.3518 16.2669 13.8074 15.0931L18.448 19.7337C18.803 20.0888 19.3786 20.0888 19.7337 19.7337C20.0887 19.3787 20.0887 18.8031 19.7337 18.4481L15.093 13.8074Z"
              fill="#DCDCDC"
            />
          </svg>
        </div>
      </div>
    </header>
    <div class="filter">
      <div class="filter__domen">
        <div class="filter__domitem filter__domitem-active">
          Все
        </div>
        <div class="filter__domitem">
          Lenta.ru
        </div>
        <div class="filter__domitem">
          Mos.ru
        </div>
      </div>
      <div class="filter__image">
        <div class="filter__imgon">
          <svg
            width="18"
            height="18"
            viewBox="0 0 18 18"
            fill="none"
            xmlns="http://www.w3.org/2000/svg"
          >
            <rect
              width="18"
              height="8"
              fill="#C4C4C4"
            />
            <rect
              y="10"
              width="18"
              height="8"
              fill="#C4C4C4"
            />
          </svg>
        </div>
        <div class="filter__imgoff">
          <svg
            width="18"
            height="18"
            viewBox="0 0 18 18"
            fill="none"
            xmlns="http://www.w3.org/2000/svg"
          >
            <rect
              width="8"
              height="8"
              fill="#0029FF"
            />
            <rect
              y="10"
              width="8"
              height="8"
              fill="#0029FF"
            />
            <rect
              x="10"
              width="8"
              height="8"
              fill="#0029FF"
            />
            <rect
              x="10"
              y="10"
              width="8"
              height="8"
              fill="#0029FF"
            />
          </svg>
        </div>
      </div>
    </div>

    <div class="articles">
      <div
        v-for=" post in displayedPosts"
        :key="displayedPosts.post"
        class="articles__article article"
      >
        <div class="image-box article__image">
          <img
            v-show="imgOn"
            class="image-box__image"
            :src="post.img"
            :alt="post.title"
          >
        </div>
        <div class="article__title">
          {{ post.title }}
        </div>
        <div class="article__content">
          {{ post.content }}
        </div>
        <a
          class="article__link"
          :href="post.link"
          target="_blank"
        >Подробнее</a>
        <div class="article__footer">
          <div class="article__url">
            www.mos.ru
          </div>
          <div class="article__date">
            10.01.2020
          </div>
        </div>
      </div>
    </div>
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
  </div>
</template>

<script>
export default {
  filters: {},
  data() {
    return {
      title: 'Список новостей',
      posts: [''],
      page: 1,
      perPage: 4,
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
        }
        return false;
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
  },
};
</script>

<style lang="scss">
    body {
        background-color: #FBFBFB;
        color: #000;
    }

    h1 {
        font-family: Arial, serif;
        font-style: normal;
        font-weight: bold;
        font-size: 36px;
        line-height: 41px;
    }

    .container {
        max-width: 1060px;
        margin: 0 auto;
        display: flex;
        flex-direction: column;
    }

    .header {

      &__wrap {
        display: flex;
        justify-content: space-between;
        border-bottom: #E5E5E5 solid 1px;
        padding: 36px 0 36px 0;
        align-items: center;

      }
      &__title {
        display: flex;
        align-items: center;
      }
      &__search {
        display: flex;
        align-items: center;
      }
      &__update{
        display: flex;
        align-items: center;
        background: #fff;
        border-radius: 50%;
        padding: 8px;
        margin-left: 15px;
      }
    }
    .filter {
      display: flex;
      justify-content: space-between;
      padding: 26px 0 28px 0;
      font-size: 14px;
      font-weight: bold;
      &__domitem {
        &-active {
          color: #000000;
        }
        padding-right: 6px;
        color: #0029FF;
      }

      &__domen, &__image {
        display: flex;
      }
    }
  .article {
    padding: 30px;
    background-color: #ffffff;
    &__image {
    }
  }
   .image-box {
     background-color: orangered;
     height: 100px;
     width: 200px;
     overflow: hidden;
     &__image {
       max-width: 100%;
       height: auto;
       display: block;
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
  }
  .pagination {
    display: flex;
    font-size: 18px;
    font-weight: bold;
    &__item {
      padding: 10px;
    }

  }

</style>
