<script>
    import { ref, onMounted } from "vue";
    export default {
      name: 'Posts',
      props: {
      },
      setup() {
          const data = ref(null);
          const loading = ref(true);
          const error = ref(null);

          function fetchData() {
            loading.value = true;
            return fetch('https://reqres.in/api/users?page=1', {
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
              data.value = json.data;
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

          onMounted(() => {
            fetchData();
          });

          return {
            data,
            loading,
            error
          };
      },
      methods:{
        select:function(event){
          var userId = event.currentTarget.id;
          window.location.href="./users/"+userId;
        }
      }
    }
</script>
<template>
  <div class="user" v-for="user of data" :key="user.id">
    <div class="user-info flex items-center">
      <img :src=user.avatar alt="">
      <p class="fs-400 font-semibold user-name">{{user.first_name}} {{user.last_name}}</p>
    </div>
    <div class="user-detail flex justify-between items-center">
      <p class="fs-400 font-semibold email">{{user.email}}</p>
      <router-link :to="{ name:'userDetail', params: { id: user.id}}" class="view-btn uppercase font-bold">
        View Detail
      </router-link>
    </div>
  </div>
  <p v-if="loading">
    Still loading..
  </p>
  <p v-if="error">
    {{error}}
  </p>
</template>

<style scoped>
  .user{
    display:grid;
    grid-template-columns: calc(400px - 32px) 1fr;
    margin-bottom:1.5rem;
    column-gap: calc(2rem - 32px);
    padding-right:18px;
  }
  .user-name{
    margin-left: 1.5rem;
  }
</style>
