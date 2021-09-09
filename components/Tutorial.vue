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
export default ({
  data() {
    return {
      cards: [],
      totalCards: 78,
      cardsResult: null,
    }
  },
  mounted() {
    this.cards = this.setCards(78);
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
      const firstCard = this.getRangeRandom(1, this.cards.length);
      this.cards.splice(firstCard, 1);
      const secondCard = this.getRangeRandom(1, this.cards.length);
      this.cards.splice(secondCard, 1);
      const thirdCard = this.getRangeRandom(1, this.cards.length);
      this.cards.splice(thirdCard, 1);
      this.cardsResult = `${firstCard},${secondCard},${thirdCard}`

      this.cards = this.setCards(78);
    }
  },
})
</script>

<style scoped>
</style>