<template>
  <div v-if="person" class="app">
    {{ person.name }}'s birthday is {{ person.birthday }}
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import axios from 'axios';
import Person from './types/Person';

export default defineComponent({
  name: 'App',
  components: {},
  setup() {
    const person = ref<Person>();

    const sendRequest = async () => {
      try {
        const { data } = await axios.get<Person>(
          'https://api.themoviedb.org/3/person/138?api_key=b93ec93117c867f6525ea01e82adf2aa',
        );
        person.value = data;
      } catch (error) {
        console.log(error);
      }
    };

    sendRequest();

    return {
      person,
    };
  },
});
</script>

<style></style>
