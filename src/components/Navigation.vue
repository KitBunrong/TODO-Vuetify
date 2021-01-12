<template>
  <div>
    <v-navigation-drawer v-model="drawer" app>
      <v-list-item class="py-2" :class="{ 'py-4': flat }">
        <v-icon>mdi-account-circle-outline</v-icon>
        <v-list-item-content>
          <v-list-item-title class="title pl-8">
            Kit Bunrong
          </v-list-item-title>
        </v-list-item-content>
      </v-list-item>

      <v-divider></v-divider>

      <v-list dense nav>
        <v-list-item v-for="item in items" :key="item.title" link :to="item.to">
          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <v-app-bar app color="#fff" :flat="flat" :class="{ extend: flat }">
      <v-toolbar-title class="title">KBR3.TheCreator!</v-toolbar-title>
      <v-spacer></v-spacer>
      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>
    </v-app-bar>
  </div>
</template>

<script>
export default {
  data: () => ({
    drawer: null,
    items: [
      { title: "All", icon: "mdi-clipboard-list-outline", to: "/" },
      { title: "Inbox", icon: "mdi-inbox-arrow-down-outline", to: "/inbox" },
      { title: "Today", icon: "mdi-calendar-blank", to: "/today" },
      { title: "Tomorrow", icon: "mdi-weather-sunset", to: "/tomorrow" },
      {
        title: "Upcoming",
        icon: "mdi-inbox-arrow-up-outline",
        to: "/upcoming",
      },
      { title: "Calendar", icon: "mdi-calendar-today", to: "/calendar" },
      { title: "Statistics", icon: "mdi-tray-full", to: "/statistic" },
      { title: "Logbook", icon: "mdi-book-open-outline", to: "/logbook" },
    ],
  }),
  props: {
    flat: Boolean,
  },
};
</script>

<style lang="scss">
.v-toolbar,
.v-navigation-drawer,
.v-list-item {
  transition: 0.6s !important;
}
.extend {
  height: 80px !important;
  padding-top: 10px;
}
</style>
