<template>
  <v-card >
    <v-footer
      position: absolute
      app
      class="font-weight-medium"
    >
      <v-col
        class="text-center"
        cols="12"
      >
        {{ new Date().getFullYear() }} — <strong>Vuetify</strong>
      </v-col>
    </v-footer>
  </v-card>
</template>

<script>
// @ is an alias to /src
export default {
  name: 'Footers',
  data:()=>{
    return{
        
    }
  }
}
</script>
