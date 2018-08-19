<template>
  <dl>
    <dt>{{ title }}</dt>
    <dd v-for="(item, index) in items" :key="index">{{item}}</dd>
  </dl>
</template>

<script>
export default {
  name: 'DefinitionList',
  props: {
    title: String,
    items: Array
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  @import url("../css/definitionlist.css");
</style>