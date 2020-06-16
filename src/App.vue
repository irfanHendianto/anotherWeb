<template>
  <v-app style="background-color:#F5F5F5;">
    <Navbar />
    <v-content class="mx-4">
      <router-view></router-view>
    </v-content>
    <Footers/>
  </v-app>
</template>

<script>
import Navbar from './components/Navbar'
import Footers from './components/Footers'
export default {
  name: 'App',
  components: { Navbar, Footers },
  data: () => ({
    //
  }),
};
</script>
