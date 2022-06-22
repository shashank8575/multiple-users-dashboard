<template>
  <div>
    <v-main class="main">
      <v-container class="fill-height">
        <v-row justify="center"  dense>
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
                    label="Enter your Password"
                    name="Password"
                    prepend-inner-icon="mdi-lock"
                    type="password"
                    outlined
                    placeholder="Enter your Password"
                    v-model="password" v-on:keyup.enter="login()"
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
      user_type:[],
      email: null,
      password: null,
      
    };
  },
  methods: {
    login() {
      if (this.email === "admin@gmail.com" && this.password === "admin")
       {
        const user = {email: this.email, role: 'admin'}
        localStorage.setItem('user', JSON.stringify(user));
        this.$router.push("/admin/dashboard");
      }
      else if(this.email === "user@gmail.com" && this.password === "user"){
        const user = {email: this.email, role: 'user'}
        localStorage.setItem('user', JSON.stringify(user));
        this.$router.push("/user/dashboard");
      }
      // adding new customer user
       else if(this.email === "customer@gmail.com" && this.password === "customer"){
        const user = {email: this.email, role: 'customer'}
        localStorage.setItem('user', JSON.stringify(user));
        this.$router.push("/customer/dashboard");
      }
      
    },

  },
};
</script>



<style scoped>
.row{
  justify-content: center;
  margin-top:50px;
}
</style>


