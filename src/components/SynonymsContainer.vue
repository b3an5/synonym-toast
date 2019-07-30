<template>
  <div class="container">
    <div v-bind:key="synonym.id" v-for="synonym in synonyms" class="container1">
      <Synonym v-bind:synonym="synonym" v-bind:fetchSynonym="fetchSynonym" />
    </div>
  </div>
</template>

<script>
import Synonym from "./Synonym";
export default {
  name: "SynonymsContainer",
  props: { synonyms: Array, fetchSynonym: Function },
  components: {
    Synonym
  }
};
</script>

<style>
.container {
  margin: 0 auto;
  display: flex;
  flex-wrap: wrap;
  width: 65vw;
  height: 70vh;
  overflow: auto;
  justify-content: center;
}
::-webkit-scrollbar {
  width: 0px;
  background: transparent;
}
.container1 {
  height: 10;
}
</style>


