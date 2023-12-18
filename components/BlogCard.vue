<template>
  <div class="row">
  <div v-for="item in item" :key="item.id" class="col-12 col-lg-4">
    <div class="card align-items-center w-100 d-flex justify-content-center">
      <NuxtLink :to="'blogs/'+item.id">
      <div class="card__header">
        <img :src="`https://muellif.publisist.az/${item.img}`" alt="card__image" class="card__image" width="600">
      </div>
      <div class="card__body">
        <h4>{{item.title}}</h4>
      </div>
      </NuxtLink>
    </div>
  </div>
  </div>
</template>


<script setup lang="ts">

import {postTypes} from "~/types/posts";

const props = defineProps({
  item: {
    type: Object as () => postTypes,
    required: true },
})



</script>

<style scoped>


img {
  max-width: 100%;
  height: 200px;
  display: block;
  object-fit: cover;
  object-position: top;
}

.card {
  display: flex;
  flex-direction: column;
  width: clamp(20rem, calc(20rem + 2vw), 22rem);
  overflow: hidden;
  //box-shadow: 0 .1rem 1rem rgba(0, 0, 0, 0.1);
  border-radius: 1em;
  background: #ECE9E6;
  background: linear-gradient(to right, #FFFFFF, #ECE9E6);
  margin-bottom: 30px;
border: none !important;
  box-shadow: 0px 4px 20px 0px rgba(15, 20, 34, 0.40) !important;
}



.card__body {
  padding: 1rem;
  display: flex;
  flex-direction: column;
  gap: .5rem;
  height: 130px;
  padding-bottom: 2rem;
  background: #2F3349;
}


.tag {
  align-self: flex-start;
  padding: .25em .75em;
  border-radius: 1em;
  font-size: .75rem;
}

.tag + .tag {
  margin-left: .5em;
}

.tag-blue {
  background: #56CCF2;
  background: linear-gradient(to bottom, #2F80ED, #56CCF2);
  color: #fafafa;
}

.tag-brown {
  background: #D1913C;
  background: linear-gradient(to bottom, #FFD194, #D1913C);
  color: #fafafa;
}

.tag-red {
  background: #cb2d3e;
  background: linear-gradient(to bottom, #ef473a, #cb2d3e);
  color: #fafafa;
}

.card__body h4 {
  font-size: 1.5rem;
  text-transform: capitalize;
  color: #fff;
}

.card__footer {
  display: flex;
  padding: 1rem;
  margin-top: auto;
}

.user {
  display: flex;
  gap: .5rem;
}

.user__image {
  border-radius: 50%;
}

.user__info > small {
  color: #666;
}


</style>
