<template>
  <div>
    <ul v-for="(value, name) in data" :key="value" class="list">
      <li v-if="typeof value !== 'object'">
        <strong>{{ name }}: </strong>{{ value }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'List',
  props: {
    data: {
      type: Object,
      required: true,
    },
  },
};
</script>
<style scoped>
.list {
  list-style: none;
  text-align: start;
}
</style>
