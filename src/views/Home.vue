<template>
  <div class="home">
    <v-card class="ma-10">
      <v-card-title class="pt-5">
        <div>The Library</div>
        <v-spacer></v-spacer>
        <v-text-field
          v-model="search"
          label="Search by Name or Description"
          outlined
          rounded
        ></v-text-field>
        <v-btn fab depressed>
          <v-icon>mdi-magnify</v-icon>
        </v-btn>
        <v-spacer></v-spacer>
        <v-select
          :items="categories"
          label="Outlined style"
          outlined
        ></v-select>
      </v-card-title>
      <v-data-table
        :headers="headers"
        :items="itemsList"
        :items-per-page="10"
        class="elevation-5"
      ></v-data-table>
    </v-card>
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
  }
};
</script>
