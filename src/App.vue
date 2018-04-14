<template>
    <div class="container">
        <Header :quoteCount="quotes.length" :maxQuotes="maxQuotes"></Header>
        <NewQuote @quoteAdded="quoteAdded"></NewQuote>
        <QuoteGrid :quotes="quotes" @quoteDeleted="quoteDeleted"></QuoteGrid>
        <InfoBar></InfoBar>
    </div>
</template>

<script>
  import Header from './components/Header.vue';
  import QuoteGrid from './components/QuoteGrid.vue';
  import NewQuote from './components/NewQuote.vue';
  import InfoBar from './components/InfoBar.vue';

  export default {
    components: {
      Header,
      QuoteGrid,
      NewQuote,
      InfoBar
    },
    data: function () {
      return {
        quotes: [
          'Just a quote to see',
          'test quote',
          'Just a quote to see',
          'test quote',
        ],
        maxQuotes: 5
      }
    },
    methods: {
      quoteAdded(newQuote) {
        if (this.quotes.length >= this.maxQuotes) {
          return alert('You have reached the max number of quote. Please delete a quote first.');
        }
        this.quotes.unshift(newQuote);
      },
      quoteDeleted(index) {
        this.quotes.splice(index, 1);
      }
    }
  };
</script>

<style>
</style>
