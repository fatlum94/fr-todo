<template>
  <v-app id="inspire">
    <v-navigation-drawer v-model="drawer" :mobile-breakpoint="768" app>
      <!-- <v-list-item>
        <v-list-item-content>
          <v-list-item-title class="text-h6">
            FR Todo
          </v-list-item-title>
          <v-list-item-subtitle>
            First Vue Todo
          </v-list-item-subtitle>
        </v-list-item-content>
      </v-list-item> -->
      <v-img
        lazy-src="https://picsum.photos/id/11/10/6"
        height="170"
        class="pa-4 pt-5"
        gradient="to top right, rgba(19,84,122,.5), rgba(128,208,199,.8)"
        src="https://picsum.photos/id/11/500/300"
      >
      <v-avatar size="70" class="mb-2">
      <img
        src="https://cdn.vuetifyjs.com/images/john.jpg"
        alt="Fatlum Ramadani"
      >
    </v-avatar>
      <div class="white--text text-subtitle-1 font-weight-bold">Fatlum Ramadani</div>
      <div class="white--text text-subtitle-2">Fatlum_Ramadani</div>
    </v-img>

      <!-- <v-divider></v-divider> -->

      <v-list
        dense
        nav
      >
        <v-list-item
          v-for="item in items"
          :key="item.title"
          link
          :to="item.to"
        >
          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar
      color="primary"
      dark
      prominent
      height="170"
      app
      src="https://picsum.photos/1920/1080?random"
      scroll-target="#scrolling-techniques-2"
    >
      <template v-slot:img="{ props }">
        <v-img
          v-bind="props"
          gradient="to top right, rgba(19,84,122,.5), rgba(128,208,199,.8)"
        ></v-img>
      </template>

      <v-container class="pa-0 header-container">
        <v-row >
          <v-app-bar-nav-icon @click="drawer = !drawer">
          </v-app-bar-nav-icon>
            <v-spacer />
            <search/>
        </v-row>
        <v-row >
          <v-app-bar-title class="text-h4 ml-4">
            {{ $store.state.appTitle }}
          </v-app-bar-title>
        </v-row>
        <v-row>
          <live-data-time />
        </v-row>
      </v-container>
    </v-app-bar>

    <v-main>
      <router-view></router-view>
      <snackbar />
    </v-main>
  </v-app>
</template>

<script>
  export default {
    data: () => ({ drawer: false,
    items: [
          { title: 'Todo', icon: 'mdi-format-list-checks', to:'/'},
          { title: 'About', icon: 'mdi-help-box', to:'/about'},
     ] }),
     components:{
       'snackbar': require('@/components/Shared/Snackbar.vue').default,
       'search': require('@/components/Tools/Search.vue').default,
       'live-data-time': require('@/components/Tools/LiveDateTime.vue').default
     }
  }
</script>

<style lang="sass">
  .header-container
    max-width: none !important
</style>