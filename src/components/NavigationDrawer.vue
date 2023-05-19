<template>
  <div class="navigation-drawer">
    <!-- drawer opener icon -->
    <v-app-bar-nav-icon dark @click="drawer = !drawer"> </v-app-bar-nav-icon>
    <!-- main navigation drawer -->
    <v-navigation-drawer v-model="drawer" app light absolute temporary>
      <v-divider></v-divider>
      <v-list nav dense>
        <v-list-item-group>
          <!-- navigation item components -->
          <v-list-item
            v-for="(menu, index) in menus"
            :key="index"
            :to="menu.path"
            active-class="white primary--text"
            class="py-1"
          >
            <v-list-item-icon>
              <v-icon>{{ menu.icon }}</v-icon>
            </v-list-item-icon>
            <v-list-item-title class="font-weight-bold dark--text">
              {{ menu.title }}
              </v-list-item-title>
          </v-list-item>
        </v-list-item-group>
      </v-list>
      <template v-slot:append>
        <v-list-item class="mb-10">
          <v-btn text color="error" @click="dialog = true" block>Log Out</v-btn>
        </v-list-item>
      </template>
                      <v-row justify="center">
              <v-dialog
                v-model="dialog"
                persistent
                max-width="300"
              >
                <v-card>
                  <v-card-title class="title">
                  CONFIRM
                  </v-card-title>
                  <v-card-text>
                    Are you sure to Logout?
                  </v-card-text>
                  <v-card-actions>
                    <v-spacer></v-spacer>
                    <v-btn
                      color="green darken-1"
                      text
                      @click="dialog = false"
                    >
                      CANCEL
                    </v-btn>
                    <v-btn
                      color="red darken-1"
                      text
                      @click="logOut"
                    >
                      OK
                    </v-btn>
                  </v-card-actions>
                </v-card>
              </v-dialog>
            </v-row>
    </v-navigation-drawer>

  </div>
</template>
<script>
export default {
  name: "NavigationDrawer",
  data: function () {
    return {
      dialog : false,
      drawer: false,
      menus: [
        {
          title : "ADMINS",
          icon : "admin_panel_settings",
          path : "/admins",
          role : 0,
        },
        {
          title: "USERS",
          icon: "person",
          path: "/users",
          role: 0,
        },
        {
          title: "DEVICES",
          icon: "devices",
          path: "/devices",
          role: 0,
        },
      ],
    };
  },
  methods: {
    logOut: function () {
      localStorage.removeItem("token")
      this.$router.push("/")
    },
  },
  computed: {},
};
</script>
