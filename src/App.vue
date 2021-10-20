<template>
  <div class="app">{{ name }} is {{ age }}</div>
</template>

<script lang="ts">
import { defineComponent, ref, reactive } from 'vue';
import axios from 'axios';

export default defineComponent({
  name: 'App',
  components: {},
  setup() {
    let person = reactive({});

    const sendRequest = async () => {
      try {
        const { data } = await axios.get(
          'https://api.themoviedb.org/3/person/138?api_key=b93ec93117c867f6525ea01e82adf2aa',
        );
        person = data;
      } catch (error) {
        console.log(error);
      }
    };

    sendRequest();

    return {};
  },
});
</script>

<style></style>
