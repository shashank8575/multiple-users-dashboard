<template>
  <div>
    <v-container>
      <v-row no-gutters>
        <v-col md="6">
          <v-card class="mx-auto" height="100vh" width="256">
            <v-navigation-drawer class="deep-purple accent-4" dark permanent>
              <v-list>
                <v-list-item v-for="item in items" :key="item.title" link>
                  <v-list-item-icon>
                    <v-icon>{{ item.icon }}</v-icon>
                  </v-list-item-icon>

                  <v-list-item-content>
                    <v-list-item-title>{{ item.title }}</v-list-item-title>
                  </v-list-item-content>
                </v-list-item>
              </v-list>

              <template v-slot:append>
                <div class="pa-2">
                  <v-btn block v-on:click="logout"> Log out </v-btn>
                </div>
              </template>
            </v-navigation-drawer>
          </v-card>
        </v-col>
        <v-col md="6">
          <h2>Admin Pannel</h2>
        </v-col>
      </v-row>
      <template> </template
    ></v-container>
  </div>
</template>
 


<script>
export default {
  layout: "BlankLayout",
  data() {
    return {
      items: [
        { title: "Dashboard", icon: "mdi-view-dashboard" },
        { title: "Account", icon: "mdi-account-box" },
        { title: "Admin", icon: "mdi-gavel" },
      ],
    };
  },
  methods: {
    logout() {
      localStorage.removeItem("user");
      return this.$router.push("/login");
    },
  },
  beforeMount() {
    // console.log(' before created ');
    const data = localStorage.getItem("user");
    const userData = (data && JSON.parse(data)) || { role: "" };
    // debugger;
    if (userData.role != "admin") {
      alert("You don't have access to this route");
      this.$router.back()
    }
  },
};
</script>

