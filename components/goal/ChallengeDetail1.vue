<template lang="pug">
.forum-post.px-4.pb-5

  v-item-group.pt-3.pb-0
    template(v-for='item in posts')
      v-row.d-flex.flex-column.px-4.pb-4.justify-center.mb-4
        v-card.rounded-xl.d-flex.flex-column.justify-start(
          @click=""
          :min-height="300"
          outlined
        )
          .px-4.pt-0.mb-auto
            v-row
              v-col.pt-4(:cols="2")
              v-col.pl-0(:cols="8")
              v-col.pr-0.pt-4.text-right(:cols="2")
            v-row
              v-col
                v-img(v-if="item.img" :src="img(item.img)" :style="getImgWidth")
                p.pt-5.mb-0.font-weight-bold.subtitle-1.secondary--text.text-justify {{ $strLimit(item.challenge, 300) }}
                p.pt-2.mb-0.font-weight-regular.subtitle-2.secondary--text.text-justify {{ $strLimit(item.content, 300) }}
          v-card-actions.px-4.pt-0
  v-card.v-card.rounded-xl.d-flex.flex-column.justify-start(
          @click=""
          :min-height="100"
          outlined
        )
          .px-4.pt-0.pb-1.mb-auto
            v-row
              v-col
                p.pt-2.mb-0.font-weight-bold.subtitle-2.secondary--text.text-justify {{ $strLimit("Terms and condition: ", 300) }}
                p.pt-2.mb-0.font-weight-regular.subtitle-2.secondary--text.text-justify {{ $strLimit("1. Seedify reserves right to change/cancel terms and conditions of this challenge at any time.", 300) }}
                p.pt-2.mb-0.font-weight-regular.subtitle-2.secondary--text.text-justify {{ $strLimit("2. You may enter multiple challenges at a time.", 300) }}
</template>

<script>
import { mapGetters, mapActions } from 'vuex'

export default {
  name: 'ChallengeDetail',
  components: {
  },
  props: {
    title: {
      type: String,
      default: null
    }
  },
  data () {
    return {
      posts: [
        // {
        //   id: 1,
        //   title: '(50 points)',
        //   img: 'fastfood',
        //   challenge: 'Take a Challenge',
        //   content: 'Reduce your Fast Food expenses by 30%',
        //   information: 'Last Statement cycle you have spent RM 120.00 on Fast Food. Take a challenge to reduce your Fast Food to RM 90.00 or less by next statement cycle.'

        // }
        {
          id: 2,
          title: '(30 points)',
          img: 'challenge2',
          challenge: 'Sales Volume Challenge',
          content: 'Increase Sales Volume by 10%'
        }
        // {
        //   id: 3,
        //   title: '(100 points)',
        //   img: 'game',
        //   challenge: 'Take a Challenge',
        //   content: 'Reduce your entertainment expenses by 40%'
        // }
        // {
        //   id: 4,
        //   title: '(30 points)',
        //   img: 'receipt',
        //   challenge: 'Daily Challenge',
        //   content: 'Do not request for receipt and plastic bag after purchased',
        //   information: 'You are being assigned not to reuest plastic bag but e-receipt.'
        // }

      ]
    }
  },
  computed: {
    ...mapGetters({
      widthX: 'screen/getWidthClass'
    }),
    getImgWidth () {
      return { width: `${window.innerWidth - 80}px` }
    }
  },
  methods: {
    ...mapActions({
    }),
    avatar (id) {
      return require(`../../assets/avatar/avatar${id}.jpg`)
    },
    img (name) {
      return require(`../../assets/img/${name}.jpg`)
    }
  }
}
</script>

<style lang="scss" scoped>
.min-350-width {
  min-width: 353px !important;
}

.mb-negative {
  margin-bottom: -7px;
}

</style>
