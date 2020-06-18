<template>
  <div>
    <v-app-bar  absolute app color="transparent" flat height="75">
      <v-app-bar-nav-icon @click="drawer = !drawer" class="grey lighten-4"></v-app-bar-nav-icon>
      <!-- <v-icon  @click="drawer = !drawer" style="background-color:white; border-radius:10px; margin-right:10px">
        mdi-dots-vertical
      </v-icon> -->
      <div class="ma-auto">
         <v-toolbar-title class="grey lighten-4">Sistem Gudang</v-toolbar-title>
      </div>
      
    </v-app-bar>
    <v-navigation-drawer v-model="drawer" app dark style="background-color: #9652ff;"> 
     <v-list-item>
        <v-list-item-content>
          <v-list-item-title class="title">
            Application
          </v-list-item-title>
          <v-list-item-subtitle>
            Sistem Gudang
          </v-list-item-subtitle>
        </v-list-item-content>
      </v-list-item>

      <v-divider></v-divider>

      <v-list dense nav >
        <v-list-item v-for="item in items" :key="item.title" router :to="item.route" >
          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
  </div>
</template>
<script>
// @ is an alias to /src
export default {
  name: 'Navbar',
  data:()=>{
    return{
        drawer: false,
        items: [
          { title: 'Dashboard', icon: 'mdi-view-dashboard', route: '/'},
          { title: 'About', icon: 'mdi-help-box', route: '/about' },
        ],
    }
  }
}
</script>
