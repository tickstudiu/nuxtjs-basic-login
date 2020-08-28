<template>
  <div>
    <form @submit="userRegister">
      <div>
        <label>account_id</label>
        <input type="text" v-model="form.account_id" />
      </div>
      <div>
        <label>create_by</label>
        <input type="text" v-model="form.create_by" />
      </div>
      <div>
        <label>type</label>
        <input type="number" v-model="form.type" />
      </div>
      <div>
        <label>Username</label>
        <input type="text" v-model="form.username" />
      </div>
      <div>
        <label>Password</label>
        <input type="text" v-model="form.password" />
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
      form: {
        username: 'test7@gmail.com',
        password: 'Aa123654',
        account_id: 'a',
        create_by: 'w',
        type: 7,
      },
    }
  },
  methods: {
    userRegister(event) {
      event.preventDefault()

      this.$axios
        .post('http://localhost:5000/auth/register', this.form)
        .then((res) => {
          this.$auth.loginWith('local', { data: this.form }).then((res) => {
            console.log(res)
          })
        })
    },
  },
}
</script>
