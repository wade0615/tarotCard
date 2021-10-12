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
        result:
        <br />
        <p>{{ firstCard }}</p>
        <p>{{ secondCard }}</p>
        <p>{{ thirdCard }}</p>
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
      totalCards: tarotCards.length,
      firstCard: null,
      secondCard: null,
      thirdCard: null,
      cardsResult: null,
    }
  },
  mounted() {
    // this.cards = this.setCards(5);
    this.cards = Array.from(tarotCards);
  },
  methods: {
    // setCards(num) {
    //   const cards = [];
    //   for (let i = 0; i < num; i++) {
    //     cards.push(i);
    //   };
    //   return cards;
    // },
    getRangeRandom(min,max){
      return Math.floor(Math.random()*(max-min+1))+min;
    },
    getThreeCards() {
      const firstCardIndex = this.getRangeRandom(0, this.cards.length - 1);
      this.firstCard = this.cards.splice(firstCardIndex, 1)[0].name;
      const secondCardIndex = this.getRangeRandom(0, this.cards.length - 1);
      this.secondCard = this.cards.splice(secondCardIndex, 1)[0].name;
      const thirdCardIndex = this.getRangeRandom(0, this.cards.length - 1);
      this.thirdCard = this.cards.splice(thirdCardIndex, 1)[0].name;

      // this.cards = this.setCards(5);
      this.cards = Array.from(tarotCards);
    }
  },
})
</script>

<style scoped>
</style>