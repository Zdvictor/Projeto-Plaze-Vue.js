<template>
  <div class="home">
    <NavbarComponent />
    <HomeComponent />
    <FooterComponent />
  </div>
</template>

<script>
// @ is an alias to /src
import NavbarComponent from '@/components/NavbarComponent.vue'
import HomeComponent from '../components/HomeComponent.vue'
import FooterComponent from '../components/FooterComponent.vue'


export default {
  name: 'HomeView',
  components: {
    NavbarComponent,
    HomeComponent,
    FooterComponent
  },

}
</script>
