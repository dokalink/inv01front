<template >
<div>
    {{pp}}
</div>

</template>

<script>
export default {
  name: 'CData',

  async asyncData(context) {
    const pp = await context.$axios.$get('https://inv01back.herokuapp.com/api/rss');
    return { pp };
  },
  data() {
    return {
      pp: [],
    };
  },
};

</script>

<style scoped>

</style>
