<script setup>
import TopHeader from '../components/TopHeader.vue';
import Users from '../components/Users.vue';
</script>

<template>
  <section id="users" class="content">
    <TopHeader title="Users"/>
    <div class="content-body">
      <div class="users-box">
        <h1 class="fs-500 font-bold">All Users</h1>
        <div class="user-lists-header">
          <div class="text-light-grey font-bold text-center">Full Name</div>
          <div class="text-light-grey font-bold">Email</div>
        </div>
        <div class="user-lists">
          <Users/>
        </div>
      </div>
    </div>
  </section>
</template>
<style scoped>
  .users-box{
    border:1px solid var(--clr-grey);
    box-shadow:0px 0px 5px 1px rgba(0,0,0,.4);
    border-radius: 8px;
    min-height: 80vh;
    max-height: 80vh;
    padding:32px 0;
  }
  .user-lists{
    padding-inline: 0!important;
    margin:32px;
    max-height: 500px;
    overflow: auto;
  }
  .users-box > *:not(.user-lists-header){
    padding-inline: 32px;
  }
  .user-lists-header{
    display:grid;
    grid-template-columns:400px 1fr;
    column-gap: 2rem;
    border-bottom:2px solid #DFE0EB;
    padding-bottom:1rem;
    margin-top:3rem;

  }
</style>