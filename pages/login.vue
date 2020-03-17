<template>
  <div>
    <v-card class="mx-auto" max-width="500">
      <v-toolbar color="teal mb-8" dark flat>
        <v-toolbar-title>
          <h2>Login.vue</h2>
        </v-toolbar-title>
      </v-toolbar>

      <v-card-text>
        <v-form class="mb-8">
          <v-text-field
            v-model="email"
            label="Email"
            name="email"
            type="text"
          />

          <v-text-field
            v-model="password"
            label="Password"
            name="password"
            type="password"
          />
        </v-form>

        <v-row justify="center">
          <v-btn @click="login" class="ma-2" tile outlined color="teal">
            <v-icon left>mdi-account</v-icon>
            Log in
          </v-btn>
          <v-btn @click="signup" class="ma-2" tile outlined color="teal">
            <v-icon left>mdi-account-plus</v-icon>Sign Up
          </v-btn>
        </v-row>

        <v-row justify="center">
          <v-btn @click="googleLogin" class="ma-2" tile outlined color="teal">
            <v-icon left>mdi-google</v-icon>
            Log in with Google Account
          </v-btn>
        </v-row>

        <v-row justify="center">
          <v-btn @click="logout" class="ma-2" tile outlined color="teal">
            <v-icon left>mdi-logout</v-icon>Log out
          </v-btn>
        </v-row>
      </v-card-text>

      <v-card-text v-if="this.user != null">
        <v-card class="">
          <v-card-title>
            you are logged in as:
          </v-card-title>
          <v-card-text>
            <v-row align="center" justify="center">
            <v-avatar size="32">
                <img :src="user.photoURL" alt="avatar">
            </v-avatar>
            <span class="ml-6">
              {{ user.displayName }}
            </span>
            <span class="ml-6">
              {{ user.email }}
            </span>
          </v-row>
          </v-card-text>
        </v-card>
      </v-card-text>

    </v-card>
  </div>
</template>

<script>
  import firebase from '@/plugins/firebase'

  export default {
    data() {
      return {
        user: "",
        email: "",
        password: ""
      }
    },
    mounted: function() {
      firebase.auth().onAuthStateChanged((user) => {
        console.log(user)
        if (user) {
          this.user = user
        } else {
          this.user = null
        }
      })
    },
    methods: {
      login() {
        console.log("logging in...", "email:", this.email, "password:", this.password)
        // console.log("log in")

      },
      signup() {
        console.log("sign up")
        // firebase.auth().
      },
      logout() {
        console.log("log out")
        firebase.auth().signOut()
      },
      googleLogin() {
        firebase.auth().signInWithRedirect(new firebase.auth.GoogleAuthProvider())
        // .then(data =>{
        //   console.log(data)
        // })
        // .catch(error =>{
        //   console.log(error)
        // })
      }
    },
  }
</script>

<style lang="scss" scoped>

</style>