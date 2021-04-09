<template>
  <div class="container">
    <div class="block">
      1
    </div>
    <div class="block">
      2
    </div>
    <div class="block">
      3
    </div>
    <div class="block">
      4
    </div>
    <div class="block">
      5
    </div>
    <div class="block">
      6
    </div>
    <div class="block">
      7
    </div>
    <div class="block">
      8
    </div>
    <div class="block">
      9
    </div>
    <div class="block">
      10
    </div>
  </div>
</template>

<script>
export default {
};
</script>

<style lang="scss">
  body {
    background-color: #eee;
    color: #4e4544;
    font: normal 16px sans-serif;
    }

  .container {
    display: flex;
    flex-flow: row wrap;
  }
  $primary-color: #333;
  .container{
    div:first-child{
      color: orangered;
    }
  }
  .block {
    color: $primary-color;
    div {color: orangered}
    margin: 10px;
    height: 30px;
    min-width: 150px;
    width: calc(23% - 20px);
    border: 1px solid #000;
  }
</style>
