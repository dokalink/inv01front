<template>
  <div>
    <h1 @click="dd">
      Компонент тест
    </h1>
    {{ phones }}
    <button @click="$emit('enlarge-text',55)">
      Увеличить размер текста
    </button>
  </div>
</template>
<script>
export default {
  props: {
    phones: {
      type: String,
      required: true,
    },
  },
  async asyncData(context) {
    const tt = await context.$axios.$get('https://inv01back.herokuapp.com/api/rss');
    context.rrr = tt;
  },
  data() {
    return {
      rr: '444',
      rrr: [],
      posts: [],
    };
  },
  async fetch() {
    this.posts = await this.$axios.$get('https://inv01back.herokuapp.com/api/rss');
  },
  methods: {
    dd() {
      this.phones[1] = '444';
    },
  },

};
</script>
