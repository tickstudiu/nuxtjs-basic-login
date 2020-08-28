<template>
  <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
    <a class="navbar-brand" href="#">Navbar</a>
    <button
      class="navbar-toggler"
      type="button"
      data-toggle="collapse"
      data-target="#navbarNav"
      aria-controls="navbarNav"
      aria-expanded="false"
      aria-label="Toggle navigation"
    >
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarNav">
      <ul class="navbar-nav">
        <li class="nav-item active">
          <a class="nav-link" href="#">
            Home
            <span class="sr-only">(current)</span>
          </a>
        </li>
        <li class="nav-item">
          <a class="nav-link" href="#">Features</a>
        </li>
        <li class="nav-item">
          <a class="nav-link" href="#">Pricing</a>
        </li>
      </ul>

      <!-- if user logged in -->
      <ul class="navbar-nav ml-auto" v-if="$auth.loggedIn">
        <span class="navbar-text text-white">{{ $auth.user.username }}</span>
        <li class="nav-item">
          <a class="nav-link" style="cursor: pointer;" v-on:click="userLogout">logout</a>
        </li>
      </ul>

      <ul class="navbar-nav ml-auto" v-else>

        <!-- login btn -->
        <li class="nav-item">
          <span v-if="$nuxt.$route.path == '/login'">
            <a class="nav-link active" style="cursor: pointer;">login</a>
          </span>
          <span v-else>
            <nuxt-link class="nav-link" to="/login">login</nuxt-link>
          </span>  
        </li>

        <!-- reigster btn -->
        <li class="nav-item">
          <span v-if="$nuxt.$route.path == '/register'">
            <a class="nav-link active" style="cursor: pointer;">register</a>
          </span>
          <span v-else>
            <nuxt-link class="nav-link" to="/register">register</nuxt-link>
          </span>
          
        </li>
      </ul>
      
    </div>
  </nav>
</template>

<script>
export default {
  methods: {
    userLogout(event) {
      event.preventDefault()
      this.$auth.logout()
    },
  },
}
</script>

