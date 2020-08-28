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
  middleware({ store, redirect }) {
    // If the user is not authenticated
    if (store.state.auth.loggedIn) {
      return redirect('/')
    }
  },
  data() {
    return {
      login: {
        username: 'test7@gmail.com',
        password: 'Aa123654',
      },
    }
  },
  methods: {
    userLogin(event) {
      event.preventDefault()
      this.$auth.loginWith('local', { data: this.login }).then((res) => {
        this.$toast.success('Successfully authenticated')
      })
    },
  },
}
</script>
