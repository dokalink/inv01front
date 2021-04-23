<template>
  <div class="filter__domen">
    <div
      :class="{ 'filter__domitem-active': filterDomen == '' }"
      class="filter__domitem"
      @click="$emit('filterDomen','')"
    >
      Все
    </div>
    <div
      :class="{ 'filter__domitem-active': filterDomen == 'lenta' }"
      class="filter__domitem"
      @click="$emit('filterDomen','lenta')"
    >
      Lenta.ru
    </div>
    <div
      :class="{ 'filter__domitem-active': filterDomen == 'mos' }"
      class="filter__domitem"
      @click="$emit('filterDomen','mos')"
    >
      Mos.ru
    </div>
  </div>
</template>

<script>
export default {
  props: {
    filterDomen: {
      type: String,
      default: '',
    },
  },
};
</script>

<style lang="scss">
    .filter {
        &__domen {
            cursor: pointer;
        }
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
</style>
