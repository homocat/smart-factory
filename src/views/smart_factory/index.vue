<script lang="ts" setup>
import Header from "@/views/smart_factory/components/Header.vue";
import CenterPanel from "@/views/smart_factory/components/CenterPanel.vue";
import LeftPanel from "@/views/smart_factory/components/LeftPanel.vue";
import RightPanel from "@/views/smart_factory/components/RightPanel.vue";
</script>

<template>
  <div
    class="relative flex flex-col m-0 p-0 justify-center items-center w-[100vw] h-[100vh] bg-[url('src/assets/framework/preview-11.png')]"
  >
    <Header />
    <main class="flex justify-between flex-1 w-[100vw] overflow-hidden">
      <LeftPanel />
      <CenterPanel />
      <RightPanel />
    </main>
  </div>
</template>
