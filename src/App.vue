<template>
  <v-app>
    <v-navigation-drawer app dark v-model="drawer" class="px-5 blue accent-4 custom-font">
      <div class="pr-1 py-5">
        <v-list-item>
          <v-list-item-content>
            <v-list-item-title class="title">
              Admin Panel
            </v-list-item-title>
            <v-list-item-subtitle>
              welcome
            </v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>

        <v-divider></v-divider>

        <v-list dense nav>
          <v-list-item-group
color="yellow"
      >
          <v-list-item v-for="item in items" :key="item.title" link class="my-3">
            <v-list-item-icon>
              <v-icon>{{ item.icon }}</v-icon>
            </v-list-item-icon>

            <v-list-item-content>
              <v-list-item-title >
                
                  {{ item.title }}
                
              </v-list-item-title>
            </v-list-item-content>
          </v-list-item>
          </v-list-item-group>
        </v-list>
      </div>
    </v-navigation-drawer>
    <v-navigation-drawer
      right
      app
      temporary
      dark
      v-model="drawerRight"
      class="px-2 deep-purple accent-4 custom-font "
    >
      <div class="pr-1 py-5">
        <v-list-item>
          <v-list-item-content>
            <v-list-item-title class="title"> Settings </v-list-item-title>
            <v-list-item-subtitle> Adjust you Settings</v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>

        <v-divider></v-divider>

        <v-list dense nav>
          <v-list-item link>
            <v-switch label="Night Mode" v-model="nightMode" dark color="white">
            </v-switch>
           
          </v-list-item>
        </v-list>
      </div>
    </v-navigation-drawer>
    <v-app-bar app flat outlined>
      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>

      <v-toolbar-title class="d-none d-md-inline">DashBoard</v-toolbar-title>
      <v-menu bottom :offset-y="true" rounded="lg" min-width="300" two-line>
        <template v-slot:activator="{ on, attrs }">
          <v-badge
            bordered
            left
            offset-x="40"
            offset-y="19"
            color="error"
            icon="mdi-lock"
            overlap
          >
            <v-btn icon class="ml-7 " :ripple="false" v-bind="attrs" v-on="on">
              <v-icon>mdi-bell</v-icon>
              <v-icon>mdi-chevron-down</v-icon>
            </v-btn>
          </v-badge>
        </template>
        <v-toolbar flat>
          <v-toolbar-title>Title</v-toolbar-title>

          <v-spacer></v-spacer>
          <v-btn icon>
            <v-icon>mdi-email-open-outline</v-icon>
          </v-btn>
        </v-toolbar>
        <v-divider></v-divider>
        <v-list>
          <v-list-item v-for="n in 5" :key="n" @click="() => {}">
            <v-list-item-content>
              <v-list-item-title>Option {{ n }}</v-list-item-title>

              <v-list-item-subtitle>details...</v-list-item-subtitle>
            </v-list-item-content>
            <v-tooltip bottom>
              <template v-slot:activator="{ on, attrs }">
                <v-list-item-action>
                  <v-btn icon v-bind="attrs" v-on="on">
                    <v-icon color="grey lighten-1">mdi-check</v-icon>
                  </v-btn>
                </v-list-item-action>
              </template>
              <span>Mark as Read</span>
            </v-tooltip>

            <v-list-item-action>
              <v-btn icon>
                <v-icon color="grey lighten-1">mdi-email-open-outline</v-icon>
              </v-btn>
            </v-list-item-action>
          </v-list-item>
        </v-list>
      </v-menu>
      <v-btn icon @click="showSearchBox = !showSearchBox">
        <v-icon :class="{ 'blue--text': showSearchBox }">mdi-magnify</v-icon>
      </v-btn>
      <search-box v-if="showSearchBox"></search-box>
      <v-spacer></v-spacer>

  

      <v-menu :offset-y="true" left bottom>
        <template v-slot:activator="{ on, attrs }">
          <v-btn text v-bind="attrs" v-on="on">
            Account
            <v-icon>mdi-chevron-down</v-icon>
          </v-btn>
        </template>

        <v-list>
          <v-list-item v-for="n in accountList" :key="n" @click="() => {}">
            <v-list-item-title> {{ n }}</v-list-item-title>
          </v-list-item>
        </v-list>
      </v-menu>
     
      <v-btn icon class=" " @click="drawerRight = !drawerRight">
        <v-icon>mdi-cog</v-icon>
      </v-btn>
    </v-app-bar>

    <v-main>
      <Dash />
    </v-main>
  </v-app>
</template>

<script>
import Dash from "./components/Dash";
import searchBox from "./components/searchBox.vue";

export default {
  name: "App",

  components: {
    Dash,
    searchBox,
  },
  mounted() {},
  watch: {
    nightMode: {
      handler() {
        this.$vuetify.theme.dark = this.nightMode;
      },
    },
    
  },
  data: () => ({
    accountList:['Edit ' , 'LogOut'],
    nightMode: false,
    showSearchBox: false,
    drawerRight: false,
    drawer: 1,
    items: [
      { title: "Dashboard", icon: "mdi-view-dashboard" },
      { title: "Photos", icon: "mdi-image" },
      { title: "About", icon: "mdi-help-box" },
    ],
  }),
  computed: {},
};
</script>
<style >
.custom-font .v-list-item__title ,.custom-font label{
  font-size: 18px !important;
}
</style>