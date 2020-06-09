<template>
  <div class="headline">{{ title }}</div>
</template>

<script>
  export default {
    props: {
      title: {
        type: String,
        default: ''
      }
    },
    name: 'Headline'
  }
</script>

<style scoped>
  .headline {
    font-size: 22px;
    font-family: Microsoft YaHei;
    font-weight: bold;
    color: rgba(0, 21, 41, 1);
    margin-bottom: 24px;
  }
</style>