<template>
    <div class="game-area">
        <h1 class="title">What dou you think?</h1>
        <h4 class="description">After choosing one of open cards, click to closed card</h4>
        <div class="container">
            <!-- native is modifier and gives permission to click elements which are not html elements -->
            <transition-group name="rotate-all" class="card-container" appear>
                <app-card :key="card.id" @click.native="selectedCard = card.id" :class="{ shadow: selectedCard == card.id }"
                    v-for="card in cards" :card="card">
                </app-card>
            </transition-group>
        </div>

        <div class="container" >
            <!-- mode- Birinci componentin aimationu bitdikden sonra ikincininki baslasin -->
            <transition name="rotate" mode="out-in">
                <component 
                @click.native="showCard(answer)" 
                :is="activeCard" 
                :card="answer">
                </component>
            </transition>
        </div>

    </div>
</template> 
<script>

import Card from './Card.vue'
import DefaultCard from './DefaultCard.vue'
export default {
    components: {
        appCard: Card,
        appDefaultCard: DefaultCard
    },
    created() {
        let randomPicture = Math.ceil(Math.random() * this.cards.length);
        //1-5
        this.answer = this.cards[randomPicture - 1]
    },
    data() {
        return {
            cards: [
                { id: 1, component: 'app-card', image: "/src/assets/card-1.jpg" },
                { id: 2, component: 'app-card', image: '/src/assets/card-2.jpg' },
                { id: 3, component: 'app-card', image: '/src/assets/card-3.jpg' },
                { id: 4, component: 'app-card', image: '/src/assets/card-4.jpg' },
                { id: 5, component: 'app-card', image: '/src/assets/card-5.jpg' },
            ],
            selectedCard: null,
            answer: {},
            activeCard: 'app-default-card'
        }
    },
    methods: {
        showCard(answer) {
            if(this.selectedCard==null){
               alert("Choose card!");
            }
            else{
                this.activeCard = answer.component;
                setTimeout(()=>{
                if(answer.id==this.selectedCard){
                   
                   this.$emit("activeComponentEvent", 'app-celebrate')
                }
                else{
                    
                    this.$emit("activeComponentEvent", 'app-failure')
                }
                },2000)
                
               
            }
            

        }
    }

}
</script>
<style >

.title {
   margin-top: -1px;
    text-align: center;
    color: rgb(208, 205, 205);
}
.description {
    text-align: center;
    color: rgb(208, 205, 205);
    font-size: 20px;
}
.container,
.card-container {
    display: flex;
    justify-content: center;
    align-items: center;
    margin-top: 20px;
    
}
.shadow {
    box-shadow: 0px 5px 48px rgb(109, 155, 218) !important;
    transition: box-shadow 0.5s;
}
/* For the animation of open cards */
@keyframes Rotation {
    from {
        transform: rotateY(0);
    }

    to {
        transform: rotateY(1080deg);
    }
}
/* .rotate-all-enter{

} */
.rotate-all-enter-active {
    animation: Rotation ease-in-out 2s forwards;

}
/* .rotate-all-leave{
    
}
.rotate-all-leave-active{
} */
/* For the animation of closed cards */
@keyframes rotate-in {
    from {
        transform: rotateY(90deg);
    }

    to {
        transform: rotateY(0deg);
    }
}
@keyframes rotate-out {
    from {
        transform: rotateY(0deg);
    }

    to {
        transform: rotateY(90deg);
    }
}
/* .rotate-enter{

} */
.rotate-enter-active {
    animation: rotate-in ease-in-out 1s forwards;

}
 /* .rotate-leave{
    
} */
.rotate-leave-active{
   animation: rotate-out ease-in-out 1s forwards;

} 
</style>