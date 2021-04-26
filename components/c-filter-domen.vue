<template>
  <div class="filter__domen">
    <button
      :class="{ 'filter__domitem-active': filterDomen === '' }"
      class="filter__domitem"
      @click="$emit('filterDomen','')"
    >
      Все
    </button>
    <button
      :class="{ 'filter__domitem-active': filterDomen === 'www.lenta.ru' }"
      class="filter__domitem"
      @click="$emit('filterDomen','www.lenta.ru')"
    >
      Lenta.ru
    </button>
    <button
      :class="{ 'filter__domitem-active': filterDomen === 'www.mos.ru' }"
      class="filter__domitem"
      @click="$emit('filterDomen','www.mos.ru')"
    >
      Mos.ru
    </button>
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
