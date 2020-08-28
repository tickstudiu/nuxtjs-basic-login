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
        <li class="nav-item">
          <a class="nav-link" href="#">login</a>
        </li>
        <li class="nav-item">
          <a class="nav-link" href="#">register</a>
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

      this.$auth.logout().then (res => {
        console.log(res)
      })
    },
  },
}
</script>

