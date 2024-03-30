<template>
  <header :class="{ 'night-mode': isNightMode }" class="flex justify-between border-b border-slate-300 px-10 py-8">
    <div class="flex items-center gap-4">
      <img class="w-10" src="/logo.png" alt="logo" />
      <div>
        <h2 class="text-xl font-bold uppercase">Sneaker store</h2>
        <p class="text-slate-400">best sneakers</p>
      </div>
    </div>
    <div class="flex items-center gap-10">
      <NightModeToggle />
      <ul class="flex items-center gap-10">
        <li class="flex items-center gap-3 cursor-pointer text-gray-500 hover:text-black">
          <img src="/cart.svg" alt="Cart" />
          <b>30 $.</b>
        </li>
        <li class="flex items-center gap-3 cursor-pointer text-gray-500 hover:text-black">
          <img src="/heart.svg" alt="favorites" />
          <span>Favorites</span>
        </li>
        <li class="flex items-center gap-3 cursor-pointer text-gray-500 hover:text-black">
          <img src="/profile.svg" alt="Profile" />
          <span>Profile</span>
        </li>
      </ul>
    </div>
  </header>
</template>

<script setup>
import NightModeToggle from "./NightModeToggle.vue";
</script>

<style scoped>
.night-mode {
  background-color: #000;
  color: #fff;
}
</style>