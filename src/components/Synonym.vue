<template>
  <div @click="updateSynonyms" class="synonym">
    <h3>{{synonym}}</h3>
  </div>
</template>

<script>
export default {
  name: "Synonym",
  props: { synonym: String, fetchSynonym: Function },
  methods: {
    updateSynonyms() {
      this.fetchSynonym(this.synonym);
    }
  }
};
</script>

<style>
.synonym {
  background-color: rgba(169, 107, 30, 0.7);
  color: rgb(234, 218, 188);
  text-align: center;
  font-size: 2rem;
  margin: 50px;
  padding: 50px;
  height: 75px;
  border-radius: 20px;
}
.synonym:hover {
  background-color: rgba(191, 144, 83, 0.7);
  transition: 1s;
  cursor: pointer;
}
h3 {
  margin: 0;
  margin-top: 10px;
}
</style>


