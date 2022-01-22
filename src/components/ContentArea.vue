<template>
  <div class="content-area">
    <div v-if="dataBeer !== undefined || dataBeer !== null">
      <CardBeer :beer="dataBeer" />
    </div>
    <div v-else>
      <h3>Здесь пока ничего нет.</h3>
    </div>
  </div>
</template>
<script>
import CardBeer from './CardBeer.vue';
export default {
  name: 'ContentArea',
  components: {
    CardBeer,
  },
  props: {
    dataBeer: {
      type: Array,
      required: true,
    },
  },
};
</script>
<style scope>
.content-area {
  padding: 50px;
  text-align: center;
  flex-grow: 1;
}
</style>
