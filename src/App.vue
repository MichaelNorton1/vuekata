<script setup>

import {computed, onMounted, provide, ref, watch} from "vue";
import AppHeader from "@/components/AppHeader.vue";
import AppBody from "@/components/AppBody.vue";


const data = ref(null)


const fetchData = async () => {
  return await fetch("../src/assets/data.json").then((res) => res.json()).then((json) => data.value = structuredClone(json)).catch((err) => console.log(err))
}

onMounted(() => {
  // mock an api call
  fetchData()
})


</script>

<template>


  <main>

    <AppHeader :data="data?.content?.header"></AppHeader>
    <AppBody :data="data?.content?.body"></AppBody>

  </main>
</template>

<style scoped>
main {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}


</style>
