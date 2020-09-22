<template>
  <v-container fluid>
    <v-row>
      <v-col>
        <v-textarea
          name="input-7-1"
          label="tweets"
          value=""
          hint="text fields at 140"
          ></v-textarea>
      </v-col>
    </v-row>
    <v-row>
      <v-col
        >
        <v-card
          class="pa-2"
          outlined
          v-for="item in timeline"
          :key="item.id"
          >
          <v-list-item
            three-line
            >
            <v-list-item-avatar>
              <img
                :src="`${item.icon}`"
                />
            </v-list-item-avatar>
            <v-list-item-content>
              <div class="overline">{{ item.name }}</div>
              <v-list-item-text>{{ item.tweet }}</v-list-item-text>
            </v-list-item-content>
          </v-list-item>

          <v-card-actions>
              <v-btn icon color="white" click="chat">
                <v-icon>mdi-chat-plus</v-icon>
              </v-btn>
              <v-btn icon color="deep-orange">
                <v-icon>mdi-thumb-up</v-icon>
              </v-btn>
              <v-btn icon color="indigo lighten-1">
                <v-icon>mdi-thumb-down</v-icon>
              </v-btn>
              <v-btn icon color="green">
                <v-icon>mdi-cached</v-icon>
              </v-btn>
          </v-card-actions>

          <v-textarea
            v-if="chat"
            color="white"
            hint="Hint text"
            ></v-textarea>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";

@Component({})
export default class Home extends Vue {
  chat: boolesn = false
  timeline: object[] = [
    {id: "0001", name: "Gen", icon: "https://avatars3.githubusercontent.com/u/15011235?s=460&u=5816071635b8f9a6c849e500835ee8ecc74e2449&v=4", tweet: "test tweet"},
    {id: "0002", name: "Gen", icon: "https://avatars3.githubusercontent.com/u/15011235?s=460&u=5816071635b8f9a6c849e500835ee8ecc74e2449&v=4", tweet: "test tweet"}
  ];
}
</script>
