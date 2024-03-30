<script setup>
import { onMounted, reactive, ref, watch } from "vue";
import axios from "axios";

import Header from "./components/Header.vue";
import CardList from "./components/CardList.vue";
import Drawer from "./components/Drawer.vue";

const items = ref([]);

const filters = reactive({
  sortBy: "title",
  searchQuery: "",
});

const onChangeSelect = (event) => {
  filters.sortBy = event.target.value;
};

const onChangeSearchInput = (event) => {
  filters.searchQuery = event.target.value;
};

const fetchItems = async () => {
  try {
    const params = {
      sortBy: filters.sortBy,
    };

    if (filters.searchQuery) {
      params.title = `*${filters.searchQuery}*`;
    }

    const { data } = await axios.get(
      `https://604781a0efa572c1.mokky.dev/items`,
      {
        params,
      }
    );

    function convertPrice(priceRubles, exchangeRate) {
      const priceDollars = priceRubles / exchangeRate;
      return Math.floor(priceDollars);
    }

    const exchangeRate = 92.5;

    items.value = data
      .filter((item) => item.id < 13)
      .map((item) => {
        if (item.title.includes("Мужские Кроссовки")) {
          item.title = item.title.replace(
            "Мужские Кроссовки",
            "Men's sneakers"
          );
        }

        if (item.title.includes("Кроссовки")) {
          item.title = item.title.replace("Кроссовки", "Sneakers");
        }

        item.price = convertPrice(item.price, exchangeRate);

        return item;
      });
  } catch (error) {
    console.log(error);
  }
};

onMounted(fetchItems);
watch(filters, fetchItems);
</script>

<template>
  <div class="bg-white w-4/5 m-auto rounded-xl shadow-2xl mt-14">
    <Header />
    <div class="p-10">
      <div class="flex justify-between items-center">
        <h2 class="text-3xl font-bold mb-8">All sneakers</h2>
        <div class="flex gap-4">
          <select
            @change="onChangeSelect"
            class="py-2 px-3 border rounded-md outline-none"
          >
            <option value="name">By name</option>
            <option value="price">By price (low)</option>
            <option value="-price">By price (high)</option>
          </select>
          <div class="relative">
            <img class="absolute left-4 top-3" src="/search.svg" alt="search" />
            <input
              @input="onChangeSearchInput"
              class="border rounded-md py-2 pl-11 pr-4 outline-none focus:border-gray-400"
              placeholder="Search..."
              type="text"
            />
          </div>
        </div>
      </div>
      <div class="mt-10">
        <CardList :items="items" />
      </div>
      <!-- <Drawer/> -->
    </div>
  </div>
</template>

<style scoped></style>
