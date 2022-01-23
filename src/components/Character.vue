<template>
  <div class="character">
    <div class="character_avatar">
      <img :src="character ? character.avatar : null" alt="avatar" width="300" height="300" class="avatar" />
    </div>
    <hr />
    <div>
      <ul class="list" v-for="(value, name) in character" :key="value">
        <li v-if="typeof value !== 'object' && name !== 'avatar'">
          <strong>{{ name }}:</strong> {{ value }}
        </li>
      </ul>
    </div>
    <div>
      <List :data="checkCharacterEmployment" />
      <List :data="checkCharacterAddress" />
      <List :data="character.address?.coordinates ? character.address?.coordinates : {}" />
      <List :data="checkCharacterCreditCard" />
      <List :data="checkCharacterSubscription" />
    </div>
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
  },
  computed: {
    checkCharacterEmployment() {
      return this.character.employment ? this.character.employment : {};
    },
    checkCharacterAddress() {
      return this.character.address ? this.character.address : {};
    },
    checkCharacterCreditCard() {
      return this.character.credit_card ? this.character.credit_card : {};
    },
    checkCharacterSubscription() {
      return this.character.subscription ? this.character.subscription : {};
    },
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
  background-color: white;
}
.avatar {
  border-radius: 50%;
}
.list {
  list-style: none;
  text-align: start;
}
</style>
