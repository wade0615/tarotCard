<!-- Please remove this file from your project -->
<template>
  <main class="relative flex items-top justify-center min-h-screen bg-gray-100 sm:items-center sm:pt-0">
    <div class="w-1/3 outline-black text-center">
      <section class="py-3">
        {{ totalCards }}張牌
      </section>
      <button class="w-2/3 py-6 bg-yellow-500 rounded-full
        focus:outline-none focus:ring-2 focus:ring-yellow-500 focus:ring-opacity-50"
        @click="getThreeCards">
        抽牌！
      </button>
      <section class="py-3">
        result: {{ cardsResult }}
      </section>
    </div>
  </main>
</template>

<script>
import tarotCards from "@/static/cards/index.js";

export default ({
  data() {
    return {
      cards: [],
      totalCards: 78,
      cardsResult: null,
    }
  },
  mounted() {
    console.log(tarotCards);
    this.cards = this.setCards(5);
  },
  methods: {
    setCards(num) {
      const cards = [];
      for (let i = 0; i < num; i++) {
        cards.push(i);
      };
      return cards;
    },
    getRangeRandom(min,max){
      return Math.floor(Math.random()*(max-min+1))+min;
    },
    getThreeCards() {
      const firstCardIndex = this.getRangeRandom(1, this.cards.length);
      const firstCard = this.cards.splice(firstCardIndex, 1);
      console.log(this.cards.length);
      const secondCardIndex = this.getRangeRandom(1, this.cards.length);
      const secondCard = this.cards.splice(secondCardIndex, 1);
      console.log(this.cards.length);
      const thirdCardIndex = this.getRangeRandom(1, this.cards.length);
      const thirdCard = this.cards.splice(thirdCardIndex, 1);
      console.log(this.cards.length);
      // this.cardsResult = `${firstCardIndex},${secondCardIndex},${thirdCardIndex}`;
      this.cardsResult = firstCard.concat(secondCard.concat(thirdCard)).join(",");

      this.cards = this.setCards(5);
    }
  },
})
</script>

<style scoped>
</style>