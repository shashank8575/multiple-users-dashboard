<template>
  <div>
    <v-container class="mt-0">
      <!-- <v-row> -->
      <v-col>
        <v-card class="overflow-hidden" width="100%">
          <v-app-bar
            absolute
            color="#fcb69f"
            dark
            shrink-on-scroll
            src="https://picsum.photos/1920/1080?random"
            scroll-target="#scrolling-techniques-2"
          >
            <template v-slot:img="{ props }">
              <v-img
                v-bind="props"
                gradient="to top right, rgba(19,84,122,.5), rgba(128,208,199,.8)"
              ></v-img>
            </template>

            <v-app-bar-nav-icon></v-app-bar-nav-icon>

            <v-app-bar-title>Welcome to Customer Dashboard</v-app-bar-title>

            <v-spacer></v-spacer>

            <v-btn icon>
              <v-icon>mdi-magnify</v-icon>
            </v-btn>

            <v-btn icon>
              <v-icon>mdi-heart</v-icon>
            </v-btn>

            <v-btn icon>
              <v-icon>mdi-dots-vertical</v-icon>
            </v-btn>
            <v-btn color="error" v-on:click="logOut">Log Out</v-btn>
          </v-app-bar>
          <v-sheet
            id="scrolling-techniques-2"
            class="overflow-y-auto"
            max-height="600"
          >
            <v-container style="height: 1000px"></v-container>
          </v-sheet>
        </v-card>
      </v-col>
      <!-- </v-row> -->
    </v-container>
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
    logOut() {
      localStorage.removeItem("user");
      return this.$router.push("/login");
    },
  },
  beforeMount() {
    // console.log(' before created ');
    const data = localStorage.getItem("user");
    const userData = (data && JSON.parse(data)) || { role: "" };
    // debugger;
    if (userData.role != "customer") {
      alert("You don't have access to this route");
      this.$router.back()
    }
  },
};
</script>

