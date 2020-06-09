<template>
  <v-layout column>
    <v-flex xs6 offset-xs3>
      <div class="white elevation-2">
        <v-toolbar flat dense class='cyan' dark>
          <v-toolbar-title>
            Register
          </v-toolbar-title>
        </v-toolbar>
        <h1>Register</h1>
        <div class="pl-4 pr-4 pt-2 pb-2">
          <input
            type="email"
            v-model="email"
            name="email"
            placeholder="email" />
          <br>
          <input
            name="password"
            v-model="password"
            type="password"
            placeholder="password" />
          <br>
          <v-button
            @click="register">
            Register</v-button>
            <br>
          <div class="error" v-html="error"></div>
        </div>
      </div>
    </v-flex>
  </v-layout>
</template>

<script>
import AuthenitcationService from '@/services/AuthenticationService'

export default {
  data () {
    return {
      email: '',
      password: '',
      error: null
    }
  },
  methods: {
    async register () {
      try {
        await AuthenitcationService.register({
          email: this.email,
          password: this.password
      })
      } catch (error) {
        this.error = error.response.data.error
      }


    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.error {
  color: red
}
</style>
