<script setup lang="ts">
import { components } from "~/slices";

const prismic = usePrismic();
const route = useRoute();
const { data: page } = useAsyncData("[home]", () =>
  prismic.client.getSingle("home")
);

useHead({
  title: page.value?.data.meta_title,
  meta: [
    {
      name: "description",
      content: page.value?.data.meta_description,
    },
  ],
});
</script>

<template>
  <h1>Star Wars Expo</h1>

  <SliceZone
    wrapper="section"
    :slices="page?.data.slices ?? []"
    :components="components"
  />
</template>
