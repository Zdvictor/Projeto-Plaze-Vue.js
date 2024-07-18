<template>

  <div class="home">
    <NavbarComponent />
    <AboutComponentVue />
    <FooterComponent />
  </div>
  
</template>

<script>
import NavbarComponent from '@/components/NavbarComponent.vue'
import FooterComponent from '../components/FooterComponent.vue'
import AboutComponentVue from '@/components/AboutComponent.vue'

export default {
    
    components: {

        NavbarComponent,
        AboutComponentVue,
        FooterComponent


    }
}
</script>

<style>

</style>