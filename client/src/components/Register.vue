<template>
        <div>
          <h1>Register</h1>
          <input
            type="Email"
            name="Email"
            v-model="email" />
          <br>
          <input
            name="Password"
            type="password"
            v-model="password" />
          <br>
          <button
            @click="register">
            Register
          </button>
        </div>
</template>
<script>
import AuthService from '@/services/AuthService'

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
      console.log('register clicked')
      try {
        const response = await AuthService.register({
          email: this.email,
          password: this.password
        })
        console.log(response.data)
      } catch (error) {
        this.error = error.response.data.error
      }
    }
  },
  // watch: {
  //   email (value) {
  //     console.log(value)
  //   }
  // },
  mounted () {
  }
}
</script>

<style scoped>
</style>
