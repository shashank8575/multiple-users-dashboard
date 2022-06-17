<template>
  <div>
    <v-main class="main">
      <v-container class="fill-height" fluid>
        <v-row align="center" justify="center" dense>
          <v-col cols="12" sm="8" md="8" lg="4">
            <v-card color="info" elevation="10">
              <v-card-text>
                <v-form class="px-5 py-5">
                  <v-text-field
                    label="Enter your email"
                    name="Email"
                    prepend-inner-icon="mdi-mail"
                    type="mail"
                    outlined
                    placeholder="Enter your Email"
                    v-model="email" 
                  ></v-text-field>
                  <v-text-field
                    label="Enter your password"
                    nam="Password"
                    prepend-inner-icon="mdi-lock"
                    type="password"
                    outlined
                    v-model="password"
                  ></v-text-field>

                  <v-btn
                    btn-success
                    class="rounded-2"
                    color="success"
                    x-large
                    block
                    dark
                    v-on:click="login"
                    >Login</v-btn
                  >
                </v-form>
              </v-card-text>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </v-main>
  </div>
</template>

<script>
export default {
  data() {
    return {
      email: "admin@gmail.com",

      password: "admin",
    };
  },
  methods: {
    login() {
      if (this.email == "admin@gmail.com" && this.password == "admin") {
        // console.log('login function called')
        alert("you are loged in");
        this.$router.push("/admin_dashboard");
      }

      // this.$router.replace('/admin_dashboard')
      // console.log("clicked");
    },
  },
};
</script>

<style>
.main {
  background: white;
  height: 100vh;
}

</style>