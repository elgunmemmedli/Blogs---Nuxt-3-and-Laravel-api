<template>
<div>
    <AppHeader :posts="true"  />
<!--                <div v-if="data?.new_posts" class="col-md-10 col-lg-8 col-xl-7">-->
<!--                    &lt;!&ndash; Post preview&ndash;&gt;-->
<!--                    <div v-for="item of data?.new_posts" :key="item.id" class="post-preview">-->
<!--                        <NuxtLink :to="'blogs/'+item.id">-->
<!--                            <h2 class="post-title">{{ item.title }}</h2>-->
<!--                            &lt;!&ndash; <h3 class="post-subtitle" v-html="item.blogcontent"> </h3> &ndash;&gt;-->
<!--                        </NuxtLink>-->
<!--                        <p class="post-meta">-->
<!--                            Posted by-->
<!--                            <a target="_blank" href="https://www.linkedin.com/in/elgun-mammadli-b4b2661a9/">Elgun Mammadli</a>-->
<!--                            {{ item.date }}-->
<!--                        </p>-->
<!--                        <hr class="my-4" />-->
<!--                    </div>-->
<!--                    &lt;!&ndash; Divider&ndash;&gt;-->
<!--                    &lt;!&ndash; <hr class="my-4" /> &ndash;&gt;-->
<!--                    &lt;!&ndash; Pager&ndash;&gt;-->
<!--                    &lt;!&ndash; <div class="d-flex justify-content-end mb-4"><a class="btn btn-primary text-uppercase" href="#!">Older Posts →</a></div> &ndash;&gt;-->
<!--                </div>-->
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

// const { data, pending, error, refresh } = await useAsyncData(
//   'mountains',
//   () => $fetch(base_url + 'data'),{
//     server : false
//   }
// );

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
