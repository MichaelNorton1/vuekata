<script setup>

import {computed, onMounted, provide, ref, watch} from "vue";
import AppHeader from "@/components/AppHeader.vue";
import AppBody from "@/components/AppBody.vue";


const data = ref(null)


const fetchData = async () => {
  return await fetch("./src/assets/data.json").then((res) => res.json()).then((json) => data.value = structuredClone(json)).catch((err) => console.log(err))
}

onMounted(() => {
  // mock an api call
  fetchData()
})


</script>

<template>


  <main>

   <AppHeader :data="data?.content?.header" ></AppHeader>
    <AppBody :data="data?.content?.body"></AppBody>

  </main>
</template>

<style scoped>
main{    display: flex;

  flex-wrap: wrap;
  justify-content: center;}

.v-enter-active,
.v-leave-active {
  transition: opacity 1s ease;
}

.v-enter-from,
.v-leave-to {
  opacity: 0;
}

.box {
  background: repeating-linear-gradient(
      45deg,
      #606dbc,
      #606dbc 10px,
      #465298 10px,
      #465298 20px
  ) repeat-y;

  border-radius: 10px;
  width: 100px;
  height: 100px;
}

.box {
  animation: slide 5s infinite linear;
}

@keyframes slide {
  0% {
    background-position-y: 0;
  }
  100% {
    background-position-y: -500px;
  }
}

header {

}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
