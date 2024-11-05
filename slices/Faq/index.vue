<script setup lang="ts">
import { type Content } from "@prismicio/client";

// The array passed to `getSliceComponentProps` is purely optional.
// Consider it as a visual hint for you when templating your slice.
defineProps(
  getSliceComponentProps<Content.FaqSlice>([
    "slice",
    "index",
    "slices",
    "context",
  ])
);
</script>

<template>
  <section
    :data-slice-type="slice.slice_type"
    :data-slice-variation="slice.variation"
  >
    <ul>
      <template v-for="item in slice.primary.repeater">
        <li>
          <p>{{ item.question }}</p>
          <PrismicRichText :field="item.answer" />
        </li>
      </template>
    </ul>
  </section>
</template>
