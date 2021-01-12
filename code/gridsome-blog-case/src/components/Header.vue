<template>
  <header class="header sticky">
    <div class="left">
      <g-link :to="{ name: 'home' }" class="home-link">
        <h2 style="margin:0">G-Blog</h2>
      </g-link>
    </div>
    <nav class="nav right">
      <g-link class="nav__link" to="/journals-list">Journal</g-link>
      <g-link class="nav__link" to="/contact">Say Hi!</g-link>
    </nav>
  </header>
</template>

<script>
export default {
  data() {
    return {};
  },
};
</script>

<style scoped>
.header {
  position: relative;
  height: 4rem;
  z-index: 10;
  background-color: rgba(33,37,41,.95);
  color: white;
  box-shadow: 0 2px 10px 1px rgba(0,0,0,.4);

  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 2rem;
}
@media (min-width: 860px) {
  .header {
    padding: 0 10rem;
  }
}
.header.sticky {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
}
.home-link {
  text-decoration: none;
}
.logo {
  height: 1.5rem;
}
.site-name {
  font-size: 0.9rem;
  font-weight: 700;
  letter-spacing: 0.05em;
  text-decoration: none;
  text-transform: uppercase;
}
.nav > * {
  font-size: 0.9rem;
  font-weight: 600;
  text-decoration: none;
  margin-top: 4px;
  margin-right: 3rem;
  padding-bottom: 4px;
  border-bottom: 1px solid;
  border-color: transparent;
  transition: border 0.15s;
}
.nav > *:last-of-type {
  margin: 0;
}
.nav > *:hover {
  border-color: inherit;
}
.nav > .active {
  border-color: inherit;
}
</style>
