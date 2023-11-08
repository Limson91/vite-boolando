<script>
import PageHeader from './components/PageHeader.vue';
import PageContent from './components/PageContent.vue';
import PageFooter from './components/PageFooter.vue';

export default {
  components: {
    PageHeader,
    PageContent,
    PageFooter
  }
}
</script>

<template>
  <PageHeader />
  <PageContent />
  <PageFooter />
</template>

<style lang="scss">
@use '../src/style/general.scss'
</style>
