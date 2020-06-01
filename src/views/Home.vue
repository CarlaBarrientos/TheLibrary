<template>
  <div class="home">
    <v-container class="my-10">
      <v-card class="pa-8">
        <v-layout row wrap justify-space-around>
          <v-flex md2>
            <div class="mt-4 ml-10">The Library</div>
          </v-flex>
          <v-flex md4>
            <v-text-field
              v-model="search"
              append-icon="mdi-magnify"
              label="Search by Name or Description"
              outlined
              rounded
            ></v-text-field>
          </v-flex>
          <v-flex md4>
            <v-select
              :items="categories"
              label="Filter by category"
              outlined
            ></v-select>
          </v-flex>
          <v-flex md12>
            <v-data-table
              :headers="headers"
              :items="filteredList"
              :items-per-page="5"
              class="elevation-5"
            ></v-data-table>
          </v-flex>
        </v-layout>
      </v-card>
    </v-container>
  </div>
</template>

<script>
export default {
  name: "Home",
  components: {},
  data() {
    return {
      search: "",
      headers: [
        { text: "Code", value: "itemCode" },
        { text: "Name", value: "itemName" },
        { text: "Description", value: "itemDescription" },
        { text: "Category", value: "itemCategory" }
      ],
      itemsList: [
        {
          itemCode: "1",
          itemName: "El Principito",
          itemDescription: "The story of a child",
          itemCategory: "Books"
        },
        {
          itemCode: "2",
          itemName: "Science",
          itemDescription: "Magazine about science",
          itemCategory: "Magazines"
        },
        {
          itemCode: "3",
          itemName: "Los Tiempos",
          itemDescription: "Newspaper of may 31, 2020 ",
          itemCategory: "Newspapers"
        },
        {
          itemCode: "4",
          itemName: "First aid kit user information",
          itemDescription: "How to use an aid kit",
          itemCategory: "Others"
        }
      ],
      categories: ["All", "Books", "Magazines", "Newspapers", "Others"]
    };
  },
  computed: {
    filteredList() {
      return this.search === ""
        ? this.itemsList
        : this.itemsList.filter(
            item =>
              item.itemName === this.search ||
              item.itemDescription === this.search
          );
    }
  }
};
</script>
