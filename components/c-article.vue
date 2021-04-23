<template>
  <div>
    <div class="article__header">
      <div
        v-show="imgOn"
        class="article__imagebox"
      >
        <img
          class="article__image"
          :src="post.img"
          :alt="post.title"
        >
      </div>
      <div>
        <h2 class="article__title">
          <a
            class="article__titlelink"
            :href="post.link"
            target="_blank"
          >{{ post.title }}</a>
        </h2>
        <div class="article__content">
          {{ post.content }}
        </div>
      </div>
    </div>

    <div class="article__footer">
      <a
        v-show="!imgOn"
        class="article__link"
        :href="post.link"
        target="_blank"
      >Подробнее</a>
      <div class="article__footer article__footer-align">
        <div class="article__url">
          {{ post.link.search('lenta.ru') !== -1 ? 'www.lenta.ru' : '' }}
          {{ post.link.search('mos.ru') !== -1 ? 'www.mos.ru' : '' }}
        </div>
        <div class="article__date">
          {{ post.date }}
        </div>
      </div>
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
    post: {
      type: Array,
      default: [],
    },
  },
};
</script>

<style lang="scss">
  .article {
    padding: 30px 30px 4px;
    background-color: #ffffff;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    box-shadow: 0px 2px 10px 0px rgba(0, 0, 0, 0.05);
    &__header{
      display: flex;
    }
    &__title {
      color: #0029FF;
      font-size: 18px;
      font-weight: 700;
      padding-bottom: 25px;
    }
    &__titlelink {
      text-decoration: none;
    }
    &__content {
      font-size: 14px;
      padding-bottom: 27px;
    }
    &__link {
      font-size: 14px;
      font-weight: 400;
      color: #0029FF;
    }
    &__imagebox {
      margin-right: 30px;
    }
    &__image {
      width: 200px;
      height: 100px;
      object-fit: cover;
    }
  }
  .article__footer {
    padding-top: 14px;
    color: #DCDCDC;
    font-size: 14px;
    &-align {
      display: flex;
      justify-content: space-between;
    }
  }
</style>
