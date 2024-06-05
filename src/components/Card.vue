<script setup>
import Image from "@/components/Image.vue";
import Text from "@/components/Text.vue";
import {provide} from "vue";

const props = defineProps(["cards"])


</script>

<template v-if="props">
  <div class="cardContainer">
    <template v-for=" card in props.cards.content">
      <div class="cardContent">
        <Image  :src="card.img"></Image>

        <Text :cardType="'cardHeader'" :content="card.cardBold"></Text>
        <Text :cardType="'cardPara'" :content="card.cardText"></Text>
      </div>
    </template>

  </div>
</template>

<style scoped>
.cardContainer {
  width: 100%;
  display: flex;

  @media screen  and (max-width: 800px) {
  flex-wrap: wrap;

  }
  .cardContent {
    width: 415px;
    display: flex;
    padding: 32px 0px;
    flex-direction: column;
    align-items: center;


    align-self: stretch;

    @media screen  and (max-width: 800px) {

      flex: auto;

    }
  }

}




</style>