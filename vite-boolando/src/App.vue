<script>
import PageHeader from './components/PageHeader.vue';
import PageContent from './components/PageContent.vue';
import PageFooter from './components/PageFooter.vue';

import productsJSON from "./db.json"

export default {
  components: {
    PageHeader,
    PageContent,
    PageFooter
  },

  data() {
    return {
      cards: productsJSON
    }
  }
}
</script>

<template>
  <PageHeader />
  <div class="container">
    <div class="row justify beetween cards-container">
      <div class="col-4" v-for="card in cards.products">
        <PageContent :card="card" />
      </div>
    </div>
  </div>
  <PageFooter />
</template>

<style lang="scss">
@use '../src/style/general.scss';

* {
  font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
}

.cards-container {
  padding: 50px 0;
  row-gap: 50px;
}
</style>
