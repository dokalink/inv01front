<template>
  <div class="header__title">
    <h1>Список новостей</h1>
    <c-update @getUpdate="$emit('getUpdate')" />
  </div>
</template>

<script>

</script>

<style lang="scss">
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

  }

</style>
