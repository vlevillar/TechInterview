<template>
  <v-container>
    <v-row>
        <v-card width="100%">
            <v-card-title>
                Data Table
            </v-card-title>
            <v-data-table
              :headers="headers"
              :items="items"
              :search="search"
              class="elevation-1"
            >
              <template v-slot:top>
                <v-toolbar flat color="white">
                  <v-spacer></v-spacer>
                  <v-text-field
                    v-model="search"
                    append-icon="mdi-magnify"
                    label="Search"
                    single-line
                    hide-details
                  ></v-text-field>
                </v-toolbar>
              </template>
            </v-data-table>
        </v-card>
    </v-row>
  </v-container>
</template>

<script>
import axios from 'axios';

export default {
  name: 'DataTable',
  data: () => ({
    search: '',
    headers: [
      { text: 'ID', value: 'id' },
      { text: 'Name', value: 'name' },
      { text: 'Brand', value: 'brand' },
      { text: 'Style', value: 'style' },
      { text: 'Ibu', value: 'ibu' },
      { text: 'Alcohol', value: 'alcohol' },
    ],
    items: [],
  }),

  created() {
    this.fetchData();
  },
  methods: {
    async fetchData() {
      const response = await axios.get('https://random-data-api.com/api/v2/beers?size=100');
      this.items = response.data;
    },
  },

};
</script>
