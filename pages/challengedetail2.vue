<template lang="pug">
.fill-height.goal-page.pa-0.ma-0
  v-row.pa-0.ma-0.upper-row
    upper-title.ma-0(:title="'Customer Rating Challenge'" :icon="'more-vertical'" @goBack="goBackToPreviousPage" :back="true")
  .scroll.scrollbar-hide.ma-0.justify-top.align-center(:style="scrollSize")
    ChallengeDetail2()
    v-row.px-6.pt-2
      v-progress-linear.rounded-xl(
        :value="67.5"
        :color="$vuetify.theme.themes.light.green"
        height="30"
      )
        template(v-slot:default="{ value }")
          strong.white--text {{ Math.ceil(value) }}% progress
      //- f-button(:label = "'Accept Challenge'" @click="Accepted()")
</template>

<script>
import { mapGetters } from 'vuex'

import UpperTitle from '../components/UpperTitle.vue'
import ChallengeDetail2 from '~/components/goal/ChallengeDetail2.vue'
import FButton from '~/components/fincare-components/FButton.vue'

export default {
  name: 'ChallengePage2',
  components: {
    UpperTitle,
    ChallengeDetail2,
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
