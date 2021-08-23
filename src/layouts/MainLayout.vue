<template>
  <div id="q-app" style="min-height: 100vh;">
    <q-layout view="hHh Lpr lff" class="shadow-2 rounded-borders">
      <q-header elevated class="bg-white">
        <q-toolbar>
        <img src="img/advotics-logo-optimize.jpg" style="height: 30px" />
          <q-space />
          <q-item>
            <q-item-section class="text-grey">
              <div class="text-caption" style="line-height: 1rem">Username</div>
              <div class="text-xsmall">Company Name</div>
            </q-item-section>
            <q-item-section avatar>
              <q-icon size="md" name="img:icons/ic_profile.svg" />
            </q-item-section>
            <q-item-section side>
            <q-btn padding="xs" size="xs" icon="img:icons/ic_logout.png" flat />
            </q-item-section>
          </q-item>
        </q-toolbar>
      </q-header>

      <q-drawer
        v-model="drawer"
        show-if-above

        :mini="miniState"
        @mouseover="miniState = false"
        @mouseout="miniState = true"

        :width="200"
        :breakpoint="500"
        bordered
        class="bg-grey-3"
      >
        <q-scroll-area class="fit">
          <q-list padding>
            <q-item clickable v-ripple>
              <q-item-section avatar>
                <q-icon name="notes"></q-icon>
              </q-item-section>
            </q-item>

            <q-item active clickable v-ripple>
              <q-item-section avatar>
              <q-btn size="sm" unelevated color="white" padding="xs" icon="img:icons/ic_dashboard.svg" />
              </q-item-section>

              <q-item-section>
                Dashboard
              </q-item-section>
            </q-item>
          </q-list>
        </q-scroll-area>
      </q-drawer>

      <q-page-container>
        <q-page padding class="bg-background">
          <router-view />
        </q-page>
      </q-page-container>
    </q-layout>
</div>
</template>

<script>
import EssentialLink from 'components/EssentialLink.vue'

export default {
  name: 'MainLayout',
  components: { EssentialLink },
  data () {
    return {
      miniState: false,
      drawer: false,
      intervalId: null,
      dashboard: {
        title: 'Dashboard',
        icon: 'img:icons/ic_dashboard.svg',
        link: 'dashboard'
      },
    }
  }
}
</script>

<style lang="scss" scoped>
  .bg-background {
    background: $background
  }
  .q-item--active {
    background: #D2D2D2
  }
  
  @media (min-width: $breakpoint-sm) {
    .q-layout-padding {
      padding: 30px;
    }
  }
</style>
