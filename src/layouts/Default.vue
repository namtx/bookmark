<template>
  <div class="layout">
    <header class="header">
      <strong>
        <g-link to="/">{{ $static.metadata.siteName }}</g-link>
      </strong>
      <nav class="nav">
        <github-button href="https://github.com/namtx" data-show-count="true" aria-label="Follow @namtx on GitHub">Follow @namtx</github-button>
      </nav>
    </header>
    <slot/>
  </div>
</template>

<script>
import GithubButton from 'vue-github-button'

export default {
  components: {
    GithubButton
  },
  // ...
}
</script>
<static-query>
query {
  metadata {
    siteName
  }
}
</static-query>

<style lang="scss">
body {
  font-family: -apple-system,system-ui,BlinkMacSystemFont,"Segoe UI",Roboto,"Helvetica Neue",Arial,sans-serif;
  margin:0;
  padding:0;
  line-height: 1.5;
  background-color: #282a36;
}

a {
  color: #f8f8f2;
}

.layout {
  max-width: 760px;
  margin: 0 auto;
  padding-left: 20px;
  padding-right: 20px;
}

.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
  height: 80px;

  a.active--exact.active {
    color: #bd93f9;
    text-decoration: none;
  }
}

.nav__link {
  margin-left: 20px;
}
</style>
