<template>
  <div style="overflow-x: hidden;">
    <Header />
    <nuxt />
  </div>
</template>

<style>
body {
  font-family: 'Lato', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  font-size: 16px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
}

body {
  background-color: #ededed;
}

*,
*:before,
*:after {
  box-sizing: border-box;
  margin: 0;
}
</style>
<script>
import Header from '../components/Header'
export default {
  components: { Header }
}
</script>
