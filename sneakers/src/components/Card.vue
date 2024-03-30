<script setup>
defineProps({
  title: String,
  imageURL: String,
  price: Number,
  isFavorite: Boolean,
  isAdded: Boolean,
  onClickAdd: Function,
  onFavorite: Function,
});
</script>

<template>
  <div>
    <div
      class="relative border border-slate-100 rounded-3xl p-8 cursor-pointer transition hover:-translate-y-2 hover:shadow-2xl"
    >
      <img
        :src="!isFavorite ? '/like-1.svg' : '/like-2.svg'"
        alt="like 1"
        class="absolute top-8 left-8"
        @click="onFavorite"
      />

      <img :src="imageURL" alt="Sneakers-6" />
      <p class="mt-2">{{ title }}</p>
      <div class="flex justify-between mt-5">
        <div class="flex flex-col">
          <span class="text-slate-400">Price:</span>
          <b>{{ price }} $.</b>
        </div>
        <img @click="onClickAdd" :src="!isAdded ? '/plus.svg' : '/checked.svg'" alt="plus" />
      </div>
    </div>
  </div>
</template>

<style scoped></style>
