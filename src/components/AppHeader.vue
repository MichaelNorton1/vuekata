<script setup>
import {computed, inject, ref} from "vue";
import Image from "@/components/Image.vue";
import Text from "@/components/Text.vue";

const props = defineProps(["data"])
// filter array between images and text
const images = computed(() => {
  return props.data ? props.data.filter((item) => {
    return item.type === "image"
  }) : []
})
const text = computed(() => {
  return props.data ? props.data.filter((item) => {
    return item.type !== "image"
  }) : []
})


const showInnerTransition = ref(false);

const startInnerTransition = () => {
  showInnerTransition.value = true;
};

const start = computed(() => {
  return showInnerTransition
})

</script>

<template>
  <div class="container">
    <span class=" green horizontal"></span>
    <button class="tryButton"><img src="../assets/images/ico-arrow_up.svg" alt="Icon"/>try jus mundi</button>
    <div class="left">
      <template v-if="data" v-for="(item,index) in images">

        <Image v-if="item.type ==='image'" :src="item"></Image>

      </template>
    </div>


    <div class="right">
      <TransitionGroup name="list" @after-leave="startInnerTransition()" appear>
        <template v-if="data" v-for="(item, index) in text" :key="index">
          <Text :content="item"></Text>
        </template>
      </TransitionGroup>

      <Transition name="wait" v-if="start" appear>
        <button class="access">
          <img src="../assets/images/ico.svg" alt="Icon"/>Access ICC Awards
        </button>
      </Transition>
    </div>


  </div>
  <div class="bar"><span class=" green vertical"></span><span class=" green slant"></span></div>

</template>

<style scoped>

.bar {
  display: flex;
  align-items: center;
  width: 102%;
  height: 120px;
  flex-shrink: 0;
  margin-bottom: 75px;
  background: linear-gradient(180deg, rgba(255, 255, 255, 0.00) 0%, #F5F5F5 69.79%);
  justify-content: space-between;

  .vertical {
    width: 24px;
    height: 2px;
    transform: rotate(90deg);
    flex-shrink: 0;
    margin-left: 1%;

  }

  .slant {
    width: 38.869px;
    height: 2px;
    transform: rotate(-135deg);
    flex-shrink: 0;
    margin-right: 1%
  }
}


/*Button Transition */
.wait-enter-active,
.wait-leave-active {

  transition: opacity 1s ease;
  transition-delay: 2s;
}

.wait-enter-from,
.wait-leave-to {
  opacity: 0;
}

/*** Button Transition end ***/


/*** Text List Transition ***/
.list-enter-active,
.list-leave-active {
  transition: all 0.5s ease;
  transition-delay: 1s;
}

.list-enter-from,
.list-leave-to {
  opacity: 0;
  transform: translatey(30px);

}

/*** Text List Transition ***/


.container {
  background: #FFF;
  z-index: 0;
  display: flex;
  width: 100%;
  align-items: center;
  margin-bottom: 100px;

  @media screen  and (max-width: 1230px) {

    justify-content: center;

  }

  .left {
    position: relative;


  }

  .right {
    margin-right: 1%;
    max-width: 582px;
    display: flex;
    flex: 1 0 50%;
    flex-wrap: nowrap;
    justify-content: flex-end;
    flex-direction: column;
    align-items: flex-start;
  }

  .left, .right {

    flex: 1 0 50%;
  }

  .tryButton {
    border-radius: 4px;
    background: #FFF;
    box-shadow: 0px 8px 32px 0px rgba(37, 79, 109, 0.24);
    position: absolute;
    top: 3%;
    right: 3%;
    color: #2C2B2E;
    border: none;
    height: 32px;
    display: flex;
    width: 263px;

    @media screen  and (max-width: 1100px) {
      top: 1%;

    }
  }

  button {
    cursor: pointer;
    &.access {

      @media screen  and (max-width: 1200px) {
        position: relative;
        align-self: center;

      }
    }

    color: white;
    word-wrap: none;
    font-family: Lato;
    font-size: 14px;
    font-style: normal;
    font-weight: 700;
    line-height: normal;
    letter-spacing: 2px;
    text-transform: uppercase;
    padding: 20px 32px;
    border: none;


    display: flex;
    justify-content: center;
    align-items: center;
    gap: 8px;
    border-radius: 4px;
    background: var(--secondary-blue-interaction, #009EFE);
    box-shadow: 0px 8px 32px 0px rgba(37, 79, 109, 0.24);
  }


  #containerlogo {
    box-shadow: 0px 0px 128px 0px rgba(0, 0, 0, 0.10);
    position: absolute;
    top: 0;
    left: 23%;
    z-index: 1;
    display: flex;

    justify-content: center;
    align-items: center;
    flex-shrink: 0;
    border-radius: 483px;
    background: #FFF;

    box-shadow: 0px 0px 128px 0px rgba(0, 0, 0, 0.10);

    width: 483px;
    height: 483px;
    flex-shrink: 0;
  }

  #containergif {
    z-index: -1;
    position: relative;
    left: 28%;
    top: 165px;

  }

  #containersmLogo {
    z-index: 1;

    top: 74%;
    left: 30%;
    position: absolute;
    display: flex;
    align-items: center;
    justify-content: center;

    width: 187.125px;
    height: 187.125px;
    flex-shrink: 0;
    border-radius: 483px;
    background: rgb(255, 255, 255, .01);

    box-shadow: 0px 0px 128px 0px rgba(0, 0, 0, 0.10);
  }

  .boldTextcontainer {
    width: 80%
  }

  .paraTextcontainer {
    max-width: 582px ;
    text-align: left ;

    p {
      text-align: left ;
    }
  }
}


</style>