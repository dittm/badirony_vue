<template>
  <div id="wrapper">
    <nav class="navbar py-5" style="background-color: #0a0a0a;">
      <div class="navbar-brand">
        <router-link to="/" class="navbar-item"><img src="./assets/sphere_green.png" alt="Bad Irony Logo" class="globe"></router-link>

        <a class="navbar-burger" aria-label="menu" aria-expanded="false" data-target="navbar-menu" @click="showMobileMenu = !showMobileMenu">
          <span aria-hidden="true"></span>
          <span aria-hidden="true"></span>
          <span aria-hidden="true"></span>
        </a>
      </div>

      <div class="navbar-menu" id="navbar-menu" v-bind:class="{'is-active': showMobileMenu }">
        <div class="navbar-start">
          <div class="navbar-item">
            <form method="get" action="/search">
              <div class="field has-addons">
                <div class="control">
                  <input type="text" class="input" placeholder="Search for merch" name="query">
                </div>

                <div class="control">
                  <button class="button is-secondary">
                      <span class="icon">
                      <i class="fas fa-search"></i>
                      </span>
                  </button>
                </div>
              </div>
            </form>
          </div>
        </div>

        <div class="navbar-end">
          <router-link to="/tour" class="navbar-item">Tour</router-link>
          <router-link to="/merch" class="navbar-item">Merch</router-link>
          <router-link to="/music" class="navbar-item">Music</router-link>

          <div class="navbar-item">
            <div class="buttons">
              <template v-if="$store.state.isAuthenticated">
                <router-link to="/my-account" class="button is-secondary">My account</router-link>
              </template>

              <template v-else>
                <router-link to="/log-in" class="button is-secondary">Log in</router-link>
              </template>

              <router-link to="/cart" class="button is-warning">
                <span class="icon"><i class="fas fa-shopping-cart"></i></span>
                <span>Cart ({{ cartTotalLength }})</span>
              </router-link>
            </div>
          </div>
        </div>
      </div>
    </nav>

    <div class="is-loading-bar has-text-centered" v-bind:class="{'is-loading': $store.state.isLoading }">
      <div class="lds-dual-ring"></div>
    </div>

    <section class="section">
      <router-view/>
    </section>

    <footer class="text-center text-white">
        <div class="container p-4 pb-0">
          <div class="mb-4">
            <a class="btn btn-outline-light btn-floating m-1" href="#!" role="button"
              ><i class="fab fa-facebook-f"></i
            ></a>
            <a class="btn btn-outline-light btn-floating m-1" href="#!" role="button"
              ><i class="fab fa-twitter"></i
            ></a>
            <a class="btn btn-outline-light btn-floating m-1" href="#!" role="button"
              ><i class="fab fa-instagram"></i
            ></a>
              </div>
        </div>

        <div class="text-center p-3" style="background-color: #0a0a0a">
          © 2023 Copyright:
          <a class="text-white" href="/">bad-irony.com</a>
        </div>
    </footer>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  data() {
    return {
      showMobileMenu: false,
      cart: {
        items: []
      }
    }
  },
  beforeCreate() {
    this.$store.commit('initializeStore')

    const token = this.$store.state.token

    if (token) {
        axios.defaults.headers.common['Authorization'] = "Token " + token
    } else {
        axios.defaults.headers.common['Authorization'] = ""
    }
  },
  mounted() {
    this.cart = this.$store.state.cart
  },
  computed: {
      cartTotalLength() {
          let totalLength = 0

          for (let i = 0; i < this.cart.items.length; i++) {
              totalLength += this.cart.items[i].quantity
          }

          return totalLength
      }
  }
}
</script>

<style lang="scss">
@import '../node_modules/bulma';

.lds-dual-ring {
  display: inline-block;
  width: 80px;
  height: 80px;
}
.lds-dual-ring:after {
  content: " ";
  display: block;
  width: 64px;
  height: 64px;
  margin: 8px;
  border-radius: 50%;
  border: 6px solid #ccc;
  border-color: #ccc transparent #ccc transparent;
  animation: lds-dual-ring 1.2s linear infinite;
}
@keyframes lds-dual-ring {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}

.is-loading-bar {
  height: 0;
  overflow: hidden;

  -webkit-transition: all 0.3s;
  transition: all 0.3s;

  &.is-loading {
    height: 80px;
  }
}

.navbar-item, .navbar-link {
    color: #fff;
}

.navbar-item img {
    max-height: 3rem;
}

body {
  color: #fff;
}

h2 {
  padding: 20px;
}

h1, h2 {
  color: #fff !important;
}

a.router-link-active.router-link-exact-active.navbar-item {
    color: #8CCDB0;
}

.trans-table, th.trans-table {
  color: #fff !important;
  background-color: transparent;
}

</style>