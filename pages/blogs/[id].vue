<template>
<div v-if="data">
<AppHeader :posts="false" :title="data.new_posts.title" :image="data.new_posts.img"/>
    <article class="mb-4">
            <div class="container px-4 px-lg-5">
                <div>
                    <div class="text-white" v-html="data?.new_posts.blogcontent">
                    </div>
                </div>
            </div>
        </article>
</div>
</template>

<script setup lang="ts">

import {postTypes} from 'types/posts'
import { useRoute } from 'vue-router';

definePageMeta({
  layout : "default",
});


const route = useRoute();
const runtimeConfig = useRuntimeConfig();
const base_url = runtimeConfig.public.apiUrl;

const {data, error} = await useAsyncData(
    'posts',
    async () => {
      const result = {
        new_posts: {} as postTypes,
      }
      result.new_posts = await $fetch(base_url + '/' + route.params.id);
      return result;
    }
);


</script>


<style>
a{
  color: #8692D0;;
}
</style>