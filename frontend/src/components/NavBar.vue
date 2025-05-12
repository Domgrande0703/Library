<template>
  <nav class="navbar navbar-expand-lg navbar-dark bg-primary text-color-white mb-4">
    <div class="container d-flex justify-content-between align-items-center">
      <a class="navbar-brand" href="#">Library System</a>

      <!-- Hamburger Toggle Button -->
      <button
        class="navbar-toggler"
        type="button"
        @click="isNavCollapsed = !isNavCollapsed"
      >
        <span class="navbar-toggler-icon"></span>
      </button>

      <!-- Collapsible Menu -->
      <div
        class="collapse navbar-collapse"
        :class="{ show: isNavCollapsed }"
      >
        <ul class="navbar-nav me-auto mb-2 mb-lg-0">
          <li class="nav-item">
            <router-link class="nav-link" to="/">Books</router-link>
          </li>
          <li class="nav-item">
            <router-link class="nav-link" to="/borrow">Borrow</router-link>
          </li>
          <li class="nav-item">
            <router-link class="nav-link" to="/transactions">Transactions</router-link>
          </li>
        </ul>
        <button @click="logout" class="btn btn-outline-light btn-sm">Logout</button>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  data() {
    return {
      isNavCollapsed: false,
    };
  },
  methods: {
    logout() {
      localStorage.removeItem('token');
      localStorage.removeItem('user_id');
      localStorage.removeItem('username');
      this.$router.push('/login');
    },
  },
};
</script>

<style scoped>
nav {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  background-color: #5bc0de;
  z-index: 1;

}

.navbar-brand {
  color: #ffffff;
}

.navbar-brand:hover {
  color: #f8f9fa;
}

.navbar-nav .nav-link {
  color: #f8f9fa;
  font-weight: 600;
}

.navbar-nav .nav-link:hover {
  color: #0a0a0a;
  background-color: #f8f9fa;
  border-radius: 5px;
}

.btn-outline-light {
  color: #ffffff;
  border-color: #dc3545;
}

.btn-outline-light:hover {
  background-color: #dc3545;
  color: #ffffff;
}

/* Hamburger customization if needed */
.navbar-toggler {
  border: none;
  background-color: transparent;
}

/* Optional: force background on small screen */
@media (max-width: 768px) {
  nav {
    background-color: #007bff;
  }

  .navbar-nav .nav-link {
    color: #ffffff;
  }

  .btn-outline-light {
    background-color: #dc3545;
    border-color: #dc3545;
  }

  .navbar-collapse.show {
    display: block !important;
  }
}
</style>
