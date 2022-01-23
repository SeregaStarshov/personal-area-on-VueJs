<template>
  <div class="personal-area">
    <Character :character="character" />
    <ContentArea :dataBeer="arrayBeers" />
  </div>
</template>

<script>
import Character from './components/Character.vue';
import ContentArea from './components/ContentArea.vue';

export default {
  name: 'App',
  components: {
    Character,
    ContentArea,
  },
  data() {
    return {
      urlCharacter: 'https://random-data-api.com/api/users/random_user',
      urlBeers: 'https://random-data-api.com/api/beer/random_beer',
      arrayBeers: [],
      character: {},
    };
  },
  async mounted() {
    try {
      const response = await fetch(this.urlCharacter);
      const result = await response.json();
      this.character = Object.assign(result);
      const resp = await fetch(this.urlBeers);
      const data = await resp.json();
      this.arrayBeers.push(data);
    } catch (error) {
      console.log(error);
    }
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  box-sizing: border-box;
  height: 100%;
}
body {
  margin: 0;
}
ul {
  margin: 0;
  padding: 0;
}
.personal-area {
  display: flex;
  min-height: 100vh;
  flex-wrap: wrap;
}
</style>
