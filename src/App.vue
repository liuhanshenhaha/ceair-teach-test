<template>
  <div id="app">
    <img alt="Ceair logo" src="http://static-cdn.ceair.com/resource/images/public/logo_l.png?v=zh_CN_17759">
    <Examination/>
    <!-- <DefinitionList :title="definitionInfos.title" :items="definitionInfos.items" /> -->
  </div>
</template>

<script>
import Examination from './components/Examination.vue'
// import DefinitionList from './components/DefinitionList.vue'

export default {
  name: 'app',
  data: function(){
    return {
      // definitionInfos: {
      //   title: "123",
      //   items: [1,2,3,4]
      // }
    }
  },
  components: {
    Examination,
    // DefinitionList
  }
}
</script>

<style>
@import url(./css/global.css);
</style>
