<template>
  <div class="character">
    <div class="character_avatar">
      <!-- <img :src="character ? character.avatar : null" alt="avatar" width="300" height="300" class="avatar" /> -->
      <img :src="urlAvatar" alt="avatar" width="300" height="300" class="avatar" />
    </div>
    <hr />
    <div v-for="(value, name) in character" :key="value">
      <ul class="list">
        <li v-if="typeof value !== 'object' && name !== 'avatar'">
          <strong>{{ name }}:</strong> {{ value }}
        </li>
      </ul>
    </div>
    <List :data="character?.employment" />
    <List :data="character?.address" />
    <List :data="character?.address?.coordinates" />
    <List :data="character?.credit_card" />
    <List :data="character?.subscription" />
  </div>
</template>
<script>
import List from './List.vue';

export default {
  name: 'Character',
  components: {
    List,
  },
  props: {
    character: {
      type: Object,
      required: true,
    },
    urlAvatar: String,
  },
};
</script>
<style scoped>
.character {
  background-color: lightgrey;
  border-right: 1px solid black;
  padding: 30px;
}
.character_avatar {
  border-radius: 50%;
  border: 1px solid black;
  width: 300px;
  height: 300px;
  margin: auto;
}
.avatar {
  border-radius: 50%;
}
.list {
  list-style: none;
  text-align: start;
}
</style>
