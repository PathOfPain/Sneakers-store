<script setup>
import DrawerHeader from "./DrawerHeader.vue";
import CartItemList from "./CartItemList.vue";
</script>

<template>
  <div class="fixed top-0 left-0 h-full w-full bg-black z-10 opacity-70"></div>
  <div class="bg-white w-96 h-full fixed right-0 top-0 z-20 p-8">
    <DrawerHeader />
    <CartItemList />

    <div class="flex flex-col gap-4 mt-3">
      <div class="flex gap-2">
        <span>total:</span>
        <div class="flex-1 border-b border-dashed"></div>
        <b>100 $</b>
      </div>

      <div class="flex gap-2">
        <span>tax:</span>
        <div class="flex-1 border-b border-dashed"></div>
        <b>1 $</b>
      </div>
    </div>
    <button disabled="" 
    class='transition btn-lime mt-2 w-full rounded-xl py-3 text-white disabled:bg-slate-500 cursor-pointer'>
     Place an order
    </button>
  </div>
</template>

<style scoped>


  .btn-lime {
    background-color: #4f9c4b;;
  }

  .btn-lime:hover {
    background-color: #5ed558;;
  }
</style>
