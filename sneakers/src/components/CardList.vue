<script setup>
import Card from "./Card.vue";
defineProps({
  items: Array,
});
</script>

<template>
  <div class="grid grid-cols-4 gap-5">
    <Card
      v-for="item in items"
      :key="item.id"
      :price="item.price"
      :title="item.title"
      :imageURL="item.imageUrl"
      :is-added="false"
      :is-favorite="false"
      :onClickAdd="onClickAdd"
    />
  </div>
</template>
