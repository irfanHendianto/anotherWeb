<template>
  <div class="text-right">
    <v-dialog
      v-model="dialog"
      width="500"
    >
      <template v-slot:activator="{ on, attrs }">
          
        <v-btn
          color="primary"
          dark
          v-bind="attrs"
          v-on="on"
          class="pop_up"
        >
          Add
        </v-btn>
      </template>

      <v-card>
        <v-card-title
          class="headline grey lighten-2"
          primary-title
        >
          Upload File
        </v-card-title>

        <v-card-text>
            <v-file-input multiple label="File input"></v-file-input>
        </v-card-text>

        <v-divider></v-divider>

        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn
            color="primary"
            text
            @click="dialog = !dialog"
          >
            Submit
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </div>
</template>
<script>
  export default {
    data () {
      return {
        dialog: false,
      }
    },
  }
</script>

<style>
.pop_up{
    margin-bottom: 10px;
}
</style>