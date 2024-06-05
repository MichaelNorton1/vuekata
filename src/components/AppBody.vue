<script setup>
import Text from "@/components/Text.vue";
import Card from "@/components/Card.vue";

const bodyData = defineProps(["data"])

</script>

<template>
  <div class="app-body">
    <template v-if="bodyData.data" v-for="(item,index) in bodyData.data">
      <div :id="item.type + index" v-if="item.type.includes('Text') || item.type.includes('link')" class="text">


        <template v-if="item.type==='boldText'">
          <span class=" green horizontal"></span>
          <Text :content="item"></Text>
          <span class=" green horizontal"></span>
        </template>

        <Text v-else :content="item"></Text>
      </div>
      <Card :cards="item" v-else-if="item.type=== 'cardBlock'">{{ item }}</Card>


    </template>
  </div>
</template>

<style scoped>

.horizontal {
  position: relative;
  top: 50%;
}

.text {
  &:has(span) {
    justify-content: space-between;
  }

  width: 100%;
  display: flex;
  justify-content: center;
}

.app-body {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;



  #paraText1{
    width: 470px;
    text-align: center;
    div{
      p{font-size: 16px !important;}
    }

    @media (max-width: 500px) {
      width: 100%;
    }
  }
  #quoteText0{
    width:640px
  }

  #paraText4,#paraText5{
    max-width: 862px;
    display: flex;
    align-items: center;
    justify-content: center;
    text-align: center;
  }


  @media (max-width: 500px) {
    width: 100%;
  }



}

</style>