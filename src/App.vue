<template>
  <v-app id="inspire">
    <v-app-bar
      app
      clipped-left
      color="red"
      dense
      >
      <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
        <v-toolbar-title class="mr-12 align-center">
          <span class="title">FJB SNS</span>
        </v-toolbar-title>
        <v-spacer></v-spacer>
        <v-row
          align="center"
          style="max-width: 650px"
          >
          <v-text-field
            v-model="seachword"
            :append-icon-cb="() => {}"
            placeholder="Search..."
            single-line
            append-icon="mdi-magnify"
            color="white"
            hide-details
            ></v-text-field>
        </v-row>
    </v-app-bar>

    <v-navigation-drawer
      v-model="drawer"
      app
      clipped
      >
      <v-list dense>
        <v-list-item
          v-for="item in items"
          :key="item.text"
          link
          >
          <v-list-item-action>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-action>
      <v-list-item-content>
        <v-list-item-title>
          {{ item.text }}
        </v-list-item-title>
      </v-list-item-content>
        </v-list-item>
        <v-subheader class="mt-4 grey--text text--darken-1">SUBSCRIPTIONS</v-subheader>
        <v-list>
          <v-list-item
            v-for="item in users"
            :key="item.name"
            link
            >
            <v-list-item-avatar>
              <img
                :src="`https://avatars3.githubusercontent.com/u/${item.picture}`"
                alt=""
                >
            </v-list-item-avatar>
              <v-list-item-title v-text="item.name"></v-list-item-title>
          </v-list-item>
        </v-list>
        <v-list-item
          class="mt-4"
          link
          >
          <v-list-item-action>
            <v-icon color="grey darken-1">mdi-plus-circle-outline</v-icon>
          </v-list-item-action>
          <v-list-item-title class="grey--text text--darken-1">Browse Channels</v-list-item-title>
        </v-list-item>
        <v-list-item link>
          <v-list-item-action>
            <v-icon color="grey darken-1">mdi-cog</v-icon>
          </v-list-item-action>
          <v-list-item-title class="grey--text text--darken-1">Manage Subscriptions</v-list-item-title>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>


    <v-main>
      <v-container class="fill-height">
        <router-view></router-view>,
      </v-container>
    </v-main>
  </v-app>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";

@Component({})
export default class App extends Vue {
  // variuable
  drawer: any = null
  items: object[] =  [
    { icon: 'mdi-trending-up', text: 'HOME' },
    { icon: 'mdi-youtube-subscription', text: '通知' },
    { icon: 'mdi-history', text: 'メッセージ' },
    { icon: 'mdi-playlist-play', text: 'プロフィール' },
  ]

  users: object[] = [
    { picture: "15011235?s=460&u=5816071635b8f9a6c849e500835ee8ecc74e2448&v=4", name: 'Gen' },
  ]

  // methods
  created (): void {
    this.$vuetify.theme.dark = true
  }
}
</script>
