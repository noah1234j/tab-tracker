<template>

<v-layout column>
  <v-flex xs6 offset-xs3>
    <div class="white elevation-2">
      <v-toolbar flat dense class="cyan" dark>
        <v-toolbar-title>Register</v-toolbar-title>
      </v-toolbar>
        <div>
        <input type="text" name="email" placeholder="Email" v-model="email"><br>
        <input type="password" placeholder="password" name="password" v-model="password"><br>
        <div v-html="error" class="error"></div>
        <v-btn @click="register" class="blue">Register</v-btn>
        </div>
    </div>
  </v-flex>
</v-layout>
</template>

<script>
import AuthenticationService from '@/../services/AuthenticationService'

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
        const response = await AuthenticationService.register({
          email: this.email,
          password: this.password
        })
        console.log(response.data)
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
