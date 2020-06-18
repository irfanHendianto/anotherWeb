<template>
  <div class="home">
    <v-subheader>Home</v-subheader>
    <v-container>
        <v-layout row wrap justify-end class="ma-auto">
          <v-flex md1 xs12>
            <modalCreate />
          </v-flex>
          <v-flex lg1 md2 xs12 style="margin-left: 3%;">
            <Popup />
          </v-flex>
        </v-layout>
        <v-card>
          <v-card-title>
            Produk
            <v-spacer></v-spacer>
            <v-text-field
              v-model="search"
              append-icon="mdi-magnify"
              label="Search"
              single-line
              hide-details
            ></v-text-field>
          </v-card-title>
          <v-data-table
            :headers="headers"
            :items="desserts"
            :search="search"
            :items-per-page="5"
          >
            <template v-slot:item.actions="{ item }">
              <v-icon
                small
                class="mr-2"
                @click="editItem(item)"
              >
                mdi-pencil
              </v-icon>
              <v-icon
                small
                @click="deleteItem(item)"
              >
                mdi-delete
              </v-icon>
            </template>
          
          </v-data-table>
        </v-card>
    </v-container>
  </div>
</template>

<script>
// @ is an alias to /src
import Popup from '../components/Popup'
import modalCreate from '../components/ModalCreateProduct'
export default {
  name: 'Home',
  components:{Popup,modalCreate},
  data(){
    return {
        search: '',
        headers: [
          { text: 'No', value: 'id', align: 'start',},
          { text: 'Nama Produk', value: 'nama_Produk' },
          { text: 'Jumlah', value: 'jumlah' },
          { text: 'Harga', value: 'harga' },
          { text: 'Actions', value: 'actions', sortable: false },
        ],
        desserts: [
          {
            id: '1',
            nama_Produk: "Mentos",
            jumlah: 100,
            harga: "Rp."+5.000,
          },
          {
            id: '2',
            nama_Produk: "Daia",
            jumlah: 50,
            harga: "Rp."+20.000,
          },
          {
            id: '3',
            nama_Produk: "Oatmeal",
            jumlah: 20,
            harga: "Rp."+20.000,
          },
          {
            id: '4',
            nama_Produk: "Wipol",
            jumlah: 10,
            harga: "Rp."+4000,
          },
          {
            id: '5',
            nama_Produk: "Pepsodent",
            jumlah: 100,
            harga: "Rp."+25.000,
          },
          {
            id: '6',
            nama_Produk: "Formula",
            jumlah: 100,
            harga: "Rp."+15.000,
          },
          {
            id: '7',
            nama_Produk: "LifeBoy",
            jumlah: 100,
            harga: "Rp."+5000,
          },
          {
            id: '8',
            nama_Produk: "Sensodent",
            jumlah: 100,
            harga: "Rp."+28.000,
          },
          {
            id: '9',
            nama_Produk: "Oreo",
            jumlah: 20,
            harga: "Rp."+10.000,
          },
          {
            id: '10',
            nama_Produk: "Rinso",
            jumlah: 100,
            harga: "Rp."+14.000,
          },
        ],
        
     }
  },
  methods:{
    deleteItem (item) {
      console.log(item)
      const index = this.desserts.indexOf(item)
      confirm('Are you sure you want to delete this item?') && this.desserts.splice(index, 1)
    },
  }
 
}
</script>
