<template lang="pug">
v-row.pb-2.pt-3.bottom-nav.bottom-column-content-area(no-gutters)
    v-col.bottom-nav--col.px-0.mx-0(
      v-for="menu in menus"
      :key="`nav-${menu.name}`"
    )
      .bottom-btn.d-flex.flex-column.px-2.align-center
        v-card.icon-card(
          @click="goToPath(menu)"
          elevation="0"
          :color="checkRoute(menu.name)? $vuetify.theme.themes.light.primary : 'white'"
        )
          eva-icon.px-3.pb-2.pt-3(
            :name="checkRoute(menu.name) ? menu.iconFill : menu.icon"
            :fill="getButtonColor(menu.name)"
          )
        span.black--text.subtitle-1(:class="checkRoute(menu.name)? 'primary--text' : 'black--text'") {{menu.label}}
</template>

<script>
import { mapGetters, mapActions } from 'vuex'

export default {
  name: 'BottomNav',
  components: { },
  data () {
    return {
      menus: [
        {
          label: 'Home',
          path: '/home',
          name: 'home',
          icon: 'home-outline',
          iconFill: 'home'
        },
        {
          label: 'Challenge',
          path: '/challenge',
          name: 'challenge',
          icon: 'gift-outline',
          iconFill: 'gift'
        },
        {
          label: 'Upload',
          path: '/uploadpic',
          name: 'pay',
          icon: 'camera-outline',
          iconFill: 'camera'
        }
      ]
    }
  },
  computed: {
    ...mapGetters({
      currentPath: 'path/getCurrentPath'
    }),
    currentRouteName () {
      for (const menu of this.menus) {
        if (menu.name === this.$route.name) {
          return menu.name
        }
      }
      return this.currentPath
    }
  },
  methods: {
    ...mapActions({
      changeCurrentPath: 'path/changeCurrentPath'
    }),
    getButtonColor (routeName) {
      return this.currentRouteName === routeName
        ? 'white'
        : this.$vuetify.theme.themes.light.secondary
    },
    checkRoute (routeName) {
      return this.currentRouteName === routeName
    },
    goToPath (menu) {
      this.changeCurrentPath(menu.name)
      this.$router.push({
        path: menu.path
      })
    }
  }
}
</script>

<style lang="scss" scoped>
.v-btn--active {
  background-color: transparent;
}

.v-btn:not(.v-btn--round).v-size--default {
  padding: 0px !important;
}

.bottom-nav {
  position: absolute;
  bottom: 0;
  width: 100%;
  z-index: 100;
}

.bottom-column-content-area {
  border-width: 1px 0 0 0;
  border-color: rgba(193, 193, 193, 0.25);
  border-style: solid;
  background-color: white;
}

.flex.col5-custom {
  width: 20%;
  max-width: 20%;
  flex-basis: 20%;
}

:deep(.bottom-btn) {
  opacity: 1 !important;
  letter-spacing: -0.011em;
  font-size: 0.875rem;
}

.icon-card {
  border-radius: 18px;
}

</style>
