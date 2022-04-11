<script setup>
import TopHeader from '../components/TopHeader.vue';
var links = document.querySelectorAll('.menu');
links.forEach((link => {
  link.classList.remove('router-link-active')
}))
document.getElementById('aboutLink').classList.add('router-link-active');
</script>

<template>
  <section id="about" class="content">
    <TopHeader title="About"/>
    <div class="content-body">
      <div class="grid">
        <div class="grid-body">
          <h1 class="fs-600 font-bold">Lorem ipsum dolor sit.</h1>
          <div class="para flow">
            <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Dolore voluptates illo natus minus laborum quis quae iste recusandae quaerat doloribus a voluptate laboriosam cum aliquid, excepturi consectetur non ab assumenda vitae? Voluptatum ratione officia neque, nostrum possimus maxime unde magni harum repellat pariatur dolorem dolore ducimus ullam porro, aut non!</p>
            <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Dolore voluptates illo natus minus laborum quis quae iste recusandae quaerat doloribus a voluptate laboriosam cum aliquid, excepturi consectetur non ab assumenda vitae? Voluptatum ratione officia neque, nostrum possimus maxime unde magni harum repellat pariatur dolorem dolore ducimus ullam porro, aut non!</p>
          </div>
        </div>
        <div class="mx-auto img">
          <img src="/assets/about-img.png" alt="about">
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
  .para{
    --flow-space:0.5rem;
    margin-top:0.5rem;
  }
  .grid{
    grid-row-gap: 1rem;
    grid-template-columns: 1fr;
    grid-template-areas:
      'image'
      'body'
  }
  .grid-body{
    grid-area: body;
  }
  .img{
    grid-area: image;
  }

/* tablet size */
@media (min-width: 35em) {
  .para{
    --flow-space:2rem;
    margin-top:2rem;
  }
  .grid{
    grid-template-columns: minmax(400px,60%) minmax(500px,40%);
    grid-template-areas: 
    'body image';
  }
}

/* laptop size */
@media (min-width: 45em) {}
</style>
