<template>
  <transition-group name="containerSlide" mode="out-in">
  <component 
  key="mainComponent"
  @activeComponentEvent="activeComponent=$event"
  :is="activeComponent">
  </component>
  <canvas id="canvas" key="canva" v-show="activeComponent=='app-celebrate'"></canvas>
  </transition-group>
 
</template>
<script>

import GameCards from './components/GameCards.vue';
import Celebrate from './components/Celebrate.vue';
import Failure from './components/Failure.vue';
export default {
    data(){
       return{
        activeComponent: 'appGameCards'
       }
    },
   components:{
    appGameCards : GameCards,
    appCelebrate: Celebrate,
    appFailure: Failure
   }
}
</script>
<style>

body{
    font-family: sans-serif;
    background-color:#7B435B;
    overflow: hidden;
}
@keyframes slide-in {
  from{
    transform: translateX(-1000px);
    opacity: 0;
  }
  to{
    transform: translateX(0px);
    opacity: 1;
  }
}
@keyframes slide-out {
  from{
    transform: translateX(0px);
    opacity: 1;
  }
  to{
    transform: translateX(1000px);
    opacity: 0;
  }
}
/* .containerSlide-enter{

} */
.containerSlide-enter-active{
  animation: slide-in 0.5s ease-out forwards;
}
/* .containerSlide-leave{

} */
.containerSlide-leave-active{
  animation: slide-out 0.5s ease-out forwards;

}
</style>
