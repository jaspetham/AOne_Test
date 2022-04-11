<script setup>
  import { ref, onMounted } from "vue";
  import * as Vue from 'vue' // in Vue 3
  import axios from 'axios'
  import VueAxios from 'vue-axios'

  const data = ref(null);
  const loading = ref(true);
  const error = ref(null);
  function fetchData() {
    loading.value = true;
    // I prefer to use fetch
    return fetch('http://jsonplaceholder.typicode.com/posts', {
      method: 'get',
      headers: {
        'content-type': 'application/json'
      }
    })
    .then(res => {
      // a non-200 response code
      if (!res.ok) {
        // create error instance with HTTP status text
        const error = new Error(res.statusText);
        error.json = res.json();
        throw error;
      }

      return res.json();
    })
    .then(json => {
      // set the response data
      data.value = json;
    })
    .catch(err => {
      error.value = err;
      // In case a custom JSON error response was provided
      if (err.json) {
        return err.json.then(json => {
          // set the JSON response message
          error.value.message = json.message;
        });
      }
    })
    .then(() => {
      loading.value = false;
    });
  }
  fetchData();
  
  // const api = 'http://jsonplaceholder.typicode.com/posts';
  // axios.get(api).then((response) => {
  //   console.log(response.data)
  // })
</script>
<template>
  <ul v-if="!loading && data && data.length" class="mt-5 px-3">
    <li v-for="post of data" :key="post.id" class="my-3 border-2 px-5 py-4 border-orange-600">
      <div class="grid">
        <h1 class="font-bold">ID :</h1>
        <p><strong>{{post.id}}</strong></p>
      </div>
      <div class="grid">
        <h1 class="font-bold">Title :</h1>
        <p>{{post.title}}</p>
      </div>
      <div class="grid">
        <h1 class="font-bold">Desc :</h1>
        <p>{{post.body}}</p>
      </div>
    </li>
  </ul>

  <p v-if="loading">
   Still loading..
  </p>
  <p v-if="error">
    {{error}}
  </p>
</template>

<style scoped>
  .grid{
    grid-template-columns: 50px 1fr;
  }
</style>
