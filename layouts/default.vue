<template>
  <div>
    <nav class="navbar navbar-light bg-light">
      <div class="container">
        <nuxt-link :to="{name:'index'}" class="navbar-brand">
          shine
        </nuxt-link>
        <ul class="navbar-nav mr-auto">
          <li class="nav-item">
            <nuxt-link :to="{name:'posts'}" class="nav-link">Posts</nuxt-link>
          </li>
        </ul>
      </div>
    </nav>
    <div class="container">
      <nuxt />
    </div>
  </div>
</template>

<style>
.navbar-brand {
  letter-spacing: 2px;
  font-weight: bold;
}
.navbar-light .navbar-nav .nuxt-link-exact-active,
.navbar-light .navbar-nav .nuxt-link-exact-active:focus{
  color: red;
}
</style>
