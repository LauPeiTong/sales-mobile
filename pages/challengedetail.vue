<template lang="pug">
.fill-height.goal-page.pa-0.ma-0
  v-row.pa-0.ma-0.upper-row
    upper-title.ma-0(:title="'Rent Challenge'" :icon="'more-vertical'" @goBack="goBackToPreviousPage" :back="true")
  .scroll.scrollbar-hide.ma-0.justify-top.align-center(:style="scrollSize")
    ChallengeDetail()
    v-row.px-6.pt-2
      f-button(:label = "'Completed'" @click="Accepted()")
</template>

<script>
import { mapGetters } from 'vuex'
import ChallengeDetail from '~/components/goal/ChallengeDetail.vue'
import FButton from '~/components/fincare-components/FButton.vue'
export default {
  name: 'ChallengePage',
  components: {
    ChallengeDetail,
    FButton
  },
  layout: 'welcome',
  data () {
    return {
      search: null
    }
  },
  computed: {
    ...mapGetters({
      scrollSize: 'screen/getScrollClass2'
    })
  },
  methods: {
    searchBy (newValue) {
      this.search = newValue
    },
    goBackToPreviousPage () {
      this.$router.go(-1)
    },
    Accepted () {
      this.$router.push('/challengeaccepted')
    }
  }
}
</script>

<style scoped>
:deep(.scroll) {
  overflow-x: hidden;
  overflow-y: auto;
  width: 100% !important;
}

</style>
