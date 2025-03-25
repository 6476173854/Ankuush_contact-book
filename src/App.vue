<template>
  <div id="app">
    <header>
      <div class="header-content">
        <h1 class="site-title">Ankush Bansal Site</h1>
        <nav>
          <div class="nav-container">
            <router-link to="/" class="nav-link">Home</router-link>
            <router-link to="/about" class="nav-link">About</router-link>
            <router-link to="/contact" class="nav-link">Contact</router-link>
          </div>
        </nav>
      </div>
    </header>

    <main>
      <router-view></router-view>
    </main>

    <footer>
      <div class="footer-content">
        <p>&copy; 2025 Ankush Bansal. All rights reserved.</p>
      </div>
    </footer>
  </div>
</template>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: Arial, sans-serif;
  line-height: 1.6;
}

#app {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}

header {
  background-color: #2C3E50;
  color: #ECF0F1;
  padding: 20px 0;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

.header-content {
  display: flex;
  justify-content: space-between;
  align-items: center;
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
}

.site-title {
  font-size: 28px;
  font-weight: bold;
  color: #ECF0F1;
}

nav {
  display: flex;
}

.nav-container {
  display: flex;
  gap: 20px;
}

.nav-link {
  text-decoration: none;
  color: #ECF0F1;
  font-size: 18px;
  font-weight: 600;
  transition: color 0.3s ease;
}

.nav-link:hover {
  color: #3498DB;
}

main {
  padding: 20px;
  flex-grow: 1;
  background-color: #f4f4f4;
}

footer {
  background-color: #2C3E50;
  color: #ECF0F1;
  padding: 10px 0;
  text-align: center;
}

.footer-content {
  max-width: 1200px;
  margin: 0 auto;
}

footer p {
  font-size: 14px;
}
</style>
