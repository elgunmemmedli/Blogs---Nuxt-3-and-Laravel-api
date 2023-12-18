<template>
<div>
    <AppHeader :posts="true"  title="" image="" />
  <div class="container">
              <BlogCard v-if="data && data.new_posts"  :item="data.new_posts"/>
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
     result.new_posts = await $fetch(runtimeConfig.public.apiUrl);
      return result;
    }
);


</script>
