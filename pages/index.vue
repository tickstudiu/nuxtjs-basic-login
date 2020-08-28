<template>
  <div>
    <b-breadcrumb :items="items"></b-breadcrumb>
    <a style="cursor: pointer;" v-on:click="getUser">fetchUser</a>
  </div>
</template>

<script>
export default {
  middleware({ store, redirect }) {
    // If the user is not authenticated
    if (!store.state.auth.loggedIn) {
      return redirect('/login')
    } else {

    }
  },
  data() {
    return {
      items: [
        {
          text: 'home',
          href: '/',
        },
      ],
    }
  },
  methods: {
    getUser(event) {
      event.preventDefault()

      this.$auth.fetchUser().then((res) => {
        console.log(res)
      })
    },
  },
}
</script>
