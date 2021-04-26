<template>
  <div>
    fghfg
    <Test
      :phones="phones"
      @enlarge-text="rrr"
    />

  </div>
</template>

<script>
export default {
  layout: 'test',
  data() {
    return {
      phones: 'Galaxy S8',
    };
  },
  methods: {
    rrr() {
      this.phones = 'Galaxy r444';
    },
  },
};
</script>
