<script setup>
import {computed, inject, provide} from "vue";

const props = defineProps(['content', "cardType" , ])


const isCard=computed(() => {

  return props.cardType ? props.cardType :"text"


})


</script>

<template>

  <div :id="isCard" :class="(props.content.type || props.cardType) +'container'">
    <h3 v-if="props.content.type==='boldText'">{{ props.content.text }}</h3>
    <p v-else-if="props.content.type==='paraText' ">{{ props.content.text }}</p>
    <p :class="props.content.type" v-else-if="props.content.type==='quoteText'">{{ props.content.text }}</p>
    <a v-else-if="props.content.type==='link'">{{ props.content.text }}</a>
    <p :class="props.cardType" v-else-if=" props.cardType==='cardHeader'">{{ props.content }}</p>
    <p :class="props.cardType" v-else-if=" props.cardType==='cardPara'">{{ props.content }}</p>


    <div v-else>{{ props.content }}</div>
  </div>

</template>

<style scoped>
#text {
  width: 862px;
  display: flex;
  align-items: center;
  justify-content: center;
}
.cardPara{

}




.cardHeader {
  color: #2C2B2E;
  text-align: center;
  font-family: "IBM Plex Sans";
  font-size: 18px;
  font-style: normal;
  font-weight: 700;
  line-height: 0px;
}

.cardPara {
  color:  #2C2B2E;
  text-align: center;
  font-family: "IBM Plex Sans";
  font-size: 16px;

  line-height: 24px;
}

p {
  font-family: "IBM Plex Sans";
  font-size: 18px;

  line-height: 32px;

}

h3 {
  color:  #2C2B2E;
  font-kerning: none;
  font-family: Larken-ExtraBold;
  font-size: 56px;
  line-height: 64px;
  letter-spacing: -1px;
  margin-bottom: 10px;
}

.quoteTextcontainer {

  &:before {
    width: 27.968px;
    height: 19.2px;
    position: relative;
    content: url("./src/assets/images/quote_2.svg");
    bottom: 40px;
    right: 12px;
  }

  &:after {
    width: 27.968px;
    height: 19.2px;
    position: relative;
    content: url("./src/assets/images/quote_1.svg");
     top: 40px;
    left: 12px;
  }

  display: flex;
  width: 640px;
  align-items: flex-start;
  gap: 10px;
}

.quoteText {
  color: #2C2B2E;
  text-align: justify;
  font-kerning: none;

  font-family: Larken-light-italic;
  font-size: 16px;

  line-height: 32px;


}

</style>