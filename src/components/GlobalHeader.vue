<template>
  <div>
    <v-app-bar
      color="black"
      dark>
        <v-app-bar-nav-icon @click="drawer = true"></v-app-bar-nav-icon>
        <router-link class="d-flex align-center" to="/Home">
            <v-img alt="Vuetify Logo" class="shrink mr-2" contain src="../assets/icon/logo.png" width="175" />
            <v-toolbar-title style="color:white;font-size:30px;font-style:italic">管理者後台</v-toolbar-title>
        </router-link>
        <template v-slot:extension>
          <v-tabs align-with-title>
            <v-tabs-slider color="red"></v-tabs-slider>
              <v-tab>後臺主頁</v-tab>
              <v-tab>檔案管理</v-tab>
              <v-tab>註冊審核</v-tab>
              <v-tab>帳號管理</v-tab>
          </v-tabs>
        </template>
        <v-spacer> </v-spacer>
        <drop-down>
          <v-icon
            large
            color="light blue">
                mdi-translate 
            </v-icon>
        </drop-down>
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
  <template>
</template>
  </div>
</template>

<script>
  import DropDown from '../components/DropDown.vue'
  export default {
    name: 'GlobalHeader',
    components: {
    DropDown
  },
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