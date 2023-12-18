<template>
<div>
    <AppHeader :posts="true" />
  <div class="container">
    <div class="row" v-if="data?.new_posts">
              <BlogCard v-for="item of data?.new_posts" :key="item.id" :item="item"/>
            </div>
  </div>
</div>
</template>


<script setup lang="ts">


import {postTypes} from 'types/posts'

definePageMeta({
  layout : "default",
});

const runtimeConfig = useRuntimeConfig();
const base_url = runtimeConfig.public.apiUrl;


const {data, error} = await useAsyncData(
    'posts',
    async () => {
      const result = {
        new_posts: {} as postTypes,
      }
     result.new_posts = await $fetch('https://publisist.az/api/data');
      return result;
    }
);


</script>
