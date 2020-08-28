<template>
  <div>
    <form @submit="userLogin">
      <div>
        <label>Username</label>
        <input type="text" v-model="login.username" />
      </div>
      <div>
        <label>Password</label>
        <input type="text" v-model="login.password" />
      </div>
      <div>
        <button type="submit">Submit</button>
      </div>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      login: {
        username: '',
        password: '',
      },
    }
  },
  methods: {
    userLogin(event) {
      event.preventDefault()

      this.$auth.loginWith('local', { data: this.login }).then (res => {
        console.log(res)
      })
    },
  },
}
</script>
