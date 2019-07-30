<template>
  <div id="app">
    <h1 class="title">Synonym-Toast</h1>
    <h2>displaying synonyms for:</h2>
    <h2 class="current-word">{{currentWord}}</h2>
    <Form v-bind:fetchSynonym="fetchSynonym" />
    <SynonymsContainer v-bind:synonyms="synonyms" v-bind:fetchSynonym="fetchSynonym" />
  </div>
</template>

<script>
import Form from "./components/Form.vue";
import SynonymsContainer from "./components/SynonymsContainer";
import { apiKey } from "./assets/apiKey";

export default {
  name: "app",
  components: {
    Form,
    SynonymsContainer
  },
  methods: {
    async fetchSynonym(word) {
      console.log(word);
      try {
        const result = await fetch(
          `https://dictionaryapi.com/api/v3/references/thesaurus/json/${word}?key=${apiKey}`
        );
        const data = await result.json();
        this.synonyms = data[0].meta.syns.flat(1);
        this.currentWord = word;
        this.error = "";
      } catch (error) {
        this.error = "no synonyms found";
      }
    }
  },
  data() {
    return {
      synonyms: [],
      error: "",
      currentWord: "enter a word to get started"
    };
  }
};
</script>

<style>
@keyframes shadow-pulse {
  0% {
    box-shadow: 0 0 0 0px rgba(0, 0, 0, 0.2);
  }
  100% {
    box-shadow: 0 0 0 35px rgba(0, 0, 0, 0);
  }
}
.current-word {
  animation: shadow-pulse 3s infinite;
  border-radius: 10px;
  font-size: 2rem;
}
.title {
  font-size: 5rem;
  margin-top: 20px;
}
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  display: flex;
  flex-direction: column;
  align-items: center;
  color: #2c3e50;
  margin-top: 60px;
  background-image: url("https://longfordpc.com/images/toast-clipart-transparent-background-15.png");
  background-size: 100%;
  height: 93vh;
  width: 99vw;
}
</style>
