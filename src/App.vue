<template>
  <div id="app">
    <Header/>
    <main>
      <router-view/>
    </main>
    
  </div>
</template>

<script>
  import Header from './components/layouts/Header'
  import Footer from './components/layouts/Footer'
  export default {
    components: {
      Header,
      // eslint-disable-next-line vue/no-unused-components
      Footer,
    }
  }
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #10365c;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #1e3a57;
}

#nav a.router-link-exact-active {
  color: #267451;
}
#search {
  width: 50%;
  float: right;
}
</style>
