<template>
  <div class="card">
    <div>
      <ul v-for="item in beer" :key="item">
        <List :data="item" />
      </ul>
    </div>
  </div>
</template>
<script>
import List from './List.vue';
export default {
  name: 'Card',
  components: {
    List,
  },
  props: {
    beer: {
      type: Array,
      required: true,
    },
  },
};
</script>
<style>
.card {
  max-width: 400px;
  border: 1px solid black;
  padding: 20px;
  margin: auto;
}
</style>
