<script setup>
import {ref} from "vue";

const props = defineProps(['src'])
const showInnerTransition = ref(false);

const startInnerTransition = () => {
  showInnerTransition.value = true;
};


</script>

<template>


  <template v-if="props.src.image === 'smLogo'">
    <Transition name="slide-fade"  appear>
      <div :id="'container' +props.src.image"><img :id="props.src.image" :src="'../src/assets/images/' + props.src.src">
      </div>
    </Transition>
  </template>
  <template v-else-if="props.src.image === 'logo'">

    <Transition name="container" appear @after-enter="startInnerTransition()">
      <div :id="'container' +props.src.image">
        <Transition name="img" v-if="showInnerTransition" appear>
          <img :id="props.src.image" :src="'../src/assets/images/' + props.src.src">
        </Transition>
      </div>
    </Transition>

  </template>
  <div v-else :id="'container' +props.src.image">
    <img :id="props.src.image" :src="'../src/assets/images/' + props.src.src">
  </div>

</template>

<style scoped>

/*  ICC logo container */

.container-enter-active,
.container-leave-active {


  animation: createBox 1s;
}
@keyframes createBox {
  from {
    transform: scale(0);
  }
  to {
    transform: scale(1);
  }
}

/*  ICC logo Image */
.img-enter-active,
.img-leave-active {

  transition: opacity 2s ease-out;
}

.img-enter-from,
.img-leave-to {
  opacity: 0;
}

/*  JusMundi logo  */
.slide-fade-enter-active {
  left: 0;
  transition: all 0.5s ease-in;
  transition-delay: 1s;
}



.slide-fade-enter-from,
.slide-fade-leave-to {
  left: 0;
  transform: translate(-710px);
  opacity: 0;

}

/*******/


#gif {
  width: 478.981px;
  height: 496.312px;
  flex-shrink: 0;
}

#smLogo {


  width: 107.647px;
  height: 38.753px;
  flex-shrink: 0;
}


</style>