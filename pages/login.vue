<template>
  <div>
    <v-card class="mx-auto" max-width="500" height="600">
      <v-toolbar color="teal" dark flat>
        <v-toolbar-title>
          <h2>Login.vue</h2>
        </v-toolbar-title>
      </v-toolbar>

      <v-card-text>
        <v-form>
          <v-text-field
            label="Email"
            name="email"
            type="text"
          />

          <v-text-field
            label="Password"
            name="password"
            type="password"
          />
        </v-form>

        <v-row justify="center">
          <v-btn @click="Login" class="ma-2" tile outlined color="teal">
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
    </v-card>
  </div>
</template>

<script>
  export default {

  }
</script>

<style lang="scss" scoped>

</style>