<template>
  <div class="flex flex-col">
    <header
      class="flex flex-row items-center justify-center bg-cover bg-[url('src/assets/framework/preview-12.png')] w-full h-[10%]"
    >
      <template v-for="(item, index) in row" :key="index">
        <div
          class="flex-grow m-2 hover:bg-gray-800 transition text-white text-[1rem] flex justify-center items-center"
        >
          {{ item?.title }}
        </div>
      </template>
    </header>
    <main>
      <template v-for="(rowItem, rowIndex) in tableData" :key="rowIndex">
        <div
          class="flex flex-row items-center w-full h-16 even:bg-gray-700 odd:bg-gray-900"
        >
          <template v-for="(cell, cellIndex) in rowItem" :key="cellIndex">
            <div
              class="flex-grow m-2 text-[1rem] flex justify-center items-center"
            >
              {{ cell }}
            </div>
          </template>
        </div>
      </template>
    </main>
  </div>
</template>

<script lang="ts" setup>
const row = [
  { title: "Header 1" },
  { title: "Header 2" },
  { title: "Header 3" }
];
const tableData = [
  ["Row 1 Cell 1", "Row 1 Cell 2", "Row 1 Cell 3"],
  ["Row 2 Cell 1", "Row 2 Cell 2", "Row 2 Cell 3"],
  ["Row 3 Cell 1", "Row 3 Cell 2", "Row 3 Cell 3"]
];
</script>

<style scoped>
header {
  background-size: cover;
}
</style>
