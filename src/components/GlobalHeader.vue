<template>
  <div>
    <v-app-bar
      color="blue"
      dark>
        <v-app-bar-nav-icon @click="drawer = true"></v-app-bar-nav-icon>
        <router-link class="d-flex align-center" to="/Home">
            <v-img alt="Vuetify Logo" class="shrink mr-2" contain src="../assets/icon/logo.png" width="175" />
            <v-toolbar-title style="color:white;font-size:30px;font-style:italic">管理者後台</v-toolbar-title>
        </router-link>
        <v-spacer> </v-spacer>
        <v-btn target="_blank" text @click="Logout">
        <span class="mr-2">Logout</span>
        <v-icon>mdi-open-in-new</v-icon>
      </v-btn>
    </v-app-bar>

    <v-navigation-drawer
      v-model="drawer"
      absolute
      temporary
    >
      <v-list
        nav
        dense
      >
        <v-list-item-group
          v-model="group"
          active-class="dark--text text--accent-4"
        >
          <v-list-item>
            <v-list-item-icon>
              <v-icon>mdi-home</v-icon>
            </v-list-item-icon>
            <v-list-item-title>Home</v-list-item-title>
          </v-list-item>

          <v-list-item>
            <v-list-item-icon>
              <v-icon>mdi-account</v-icon>
            </v-list-item-icon>
            <v-list-item-title>Account</v-list-item-title>
          </v-list-item>
        </v-list-item-group>
      </v-list>
    </v-navigation-drawer>
  </div>
</template>

<script>
  export default {
    name: 'GlobalHeader',
    data: () => ({
      drawer: false,
      group: null,
    }),
    methods: {
        Logout(){
            this.$router.push("/");
        },
    }
  }
</script>