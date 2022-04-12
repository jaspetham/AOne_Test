<script>
    import { ref, onMounted } from "vue";
    import { useRoute } from 'vue-router'
    import axios from 'axios'
    import TopHeader from '../components/TopHeader.vue'

    export default {
        name:'UserDetail',
        props:{},
        setup() {
          const data = ref(null);
          const loading = ref(true);
          const error = ref(null);
        
            function fetchData(){
                loading.value = true;
                const route = useRoute();
                const userId = route.params.id;
                const api = "https://reqres.in/api/users/" + userId;
                axios.get(api)
                .then((response) => {
                    data.value = response.data.data;
                    console.log(response.data.data)
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
            document.getElementById('usersLink').classList.add('router-link-active');
          });

          return {
            data,
            loading,
            error
          };
      },
      components:{
          TopHeader
      }
}
</script>
<template>
    <section id="userDetail" class="content">
         <TopHeader title="Users"/>
        <div class="content-body">
             <p v-if="loading">
                Still loading..
            </p>
            <p v-if="error">
                {{error}}
            </p>
            <div v-if="!loading">
                <div class="user">
                    <h1 class="fs-600 font-semibold text-center md:text-left">{{data.first_name}} {{data.last_name}}</h1>
                    <div class="user-detail grid">
                        <img class="user-img" :src="data.avatar" alt="user">
                        <div class="details flow">
                            <div class="detail">
                                <p class="fs-400 font-semibold">First Name</p>
                                <p class="fs-400 font-semibold text-grey">{{data.first_name}}</p>
                            </div>
                            <div class="detail">
                                <p class="fs-400 font-semibold">Last Name</p>
                                <p class="fs-400 font-semibold text-grey">{{data.last_name}}</p>
                            </div>
                            <div class="detail">
                                <p class="fs-400 font-semibold">Email</p>
                                <p class="fs-400 font-semibold text-grey">{{data.email}}</p>
                            </div>
                        </div>
                    </div>
                </div>
                
                <router-link :to="{ name:'users', params: { id: '1'}}" class="view-btn uppercase font-bold fs-400">
                    Back
                </router-link>
            </div>
        </div>
    </section>
</template>
<style scoped>
    .user{
        width:100%;
        min-width: 250px;
        border:1px solid var(--clr-light-grey);
        border-radius: 8px;
        padding:1rem;
    }
    .user-img{
        border-radius: 8px;
    }
    .user-detail{
        margin-top:2rem;
        place-items: center;
        grid-template-columns: 1fr;
        row-gap: 2rem;
    }
    .view-btn{
        padding:0.5rem 2rem;
        margin-top:1.5rem;
        display:inline-flex;
    }
    /* tablet size */
    @media (min-width: 35em) {
        .user{
            width:50%;
            padding:2.5rem;
        }
        .user-detail{
            grid-template-columns: minmax(150px,200px) 1fr;
        }
        .view-btn{
            margin-top: 3rem;
        }
    }

    /* laptop size */
    @media (min-width: 45em) {}
</style>