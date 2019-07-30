<template>
  <form id="form" @submit="handleSubmit">
    <input type="text" v-model="word" />
    <input type="submit" value="enter" />
  </form>
</template>

<script>
export default {
  name: "Form",
  props: {
    fetchSynonym: Function
  },
  methods: {
    async handleSubmit(e) {
      e.preventDefault();
      await this.fetchSynonym(this.word);
      this.word = "";
    }
  },
  data() {
    return {
      word: ""
    };
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
