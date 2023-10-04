<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <aside class="sidebar">
      <!-- <SideBarMenu/> -->
      <SideBarMenu @iframe-navigation="navigateIframe" />
    </aside>
    <main class="iframe-container">
      <iframe :src="iframeSrc" class="custom-iframe"></iframe>
    </main>
  </div>
</template>

<script>
import SideBarMenu from './components/SideBarMenu.vue'
//import HelloWorld from './components/HelloWorld.vue'


export default {
  name: 'App',
  components: {
    //HelloWorld
    SideBarMenu
  },
  data() {
    return {
      iframeSrc: 'http://localhost:8082', // Set to the URL of your Home application
    };
  },
  watch: {
    // Watch for route changes
    $route(to) {
      console.log("tooooooooooooooooo", to)
      this.loadPage(to);
    },
  },
  // mounted() {
  //   // Move the route-related code to the mounted hook
  //   console.log('mounted', this.$route)
  //   this.loadPage(this.$route);
  // },
  // created() {
  //   // Load the initial page
    
  //   console .log('created', this.$route)
  //   this.loadPage(this.$route);
  // },
  methods: {
    navigateIframe(route) {
      console.log('route--------', route)
      switch (route) {
        case '/home':
          this.iframeSrc = 'http://localhost:8082'; // URL of Home application
          break;
        case '/about':
          this.iframeSrc = 'http://localhost:8083'; // URL of About application
          break;
        case 'appone/home':
          this.iframeSrc = 'http://localhost:8082'; // URL of About application
          break;
        case 'appone/about':
          console.log('comes here---------------')
          this.iframeSrc = 'http://localhost:8082/#/about'; // URL of About application
          break;
        case 'appone/contact':
          console.log('comes here---------------')
          this.iframeSrc = 'http://localhost:8082/#/contact'; // URL of About application
          break;
          case 'apptwo/home':
          this.iframeSrc = 'http://localhost:8083'; // URL of About application
          break;
        case 'apptwo/about':
          console.log('comes here---------------')
          this.iframeSrc = 'http://localhost:8083/#/about'; // URL of About application
          break;
        case 'apptwo/contact':
          console.log('comes here---------------')
          this.iframeSrc = 'http://localhost:8083/#/contact'; // URL of About application
          break;
        default:
          this.iframeSrc = 'http://localhost:8082'; // Default to Home application
          break;
      }
    },
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 0px;
  
}
.custom-iframe {
  width: calc(100% - 215px);
  left: 211px;
  
  height: 97%;
  border: 2px solid #333; /* Add a 2px solid border with color #333 */
  position: absolute;
  overflow: auto;
}
.iframe-container {
  display: flex;
  justify-content: center; /* Horizontally center the iframe */
  align-items: center; /* Vertically center the iframe */
  width: 100%;
  min-height: 98vh;
  overflow: hidden;
}
</style>
