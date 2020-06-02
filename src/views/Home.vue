<template>
  <div class="home">
    <v-container class="my-10">
      <v-card class="pa-8" color="#CDCDC0" outlined>
        <v-layout row wrap justify-space-around>
          <v-flex md2>
            <div
              class="mt-3 ml-3 brown--text headline font-italic font-weight-bold"
            >
              The Library
            </div>
          </v-flex>
          <v-flex md4>
            <v-text-field
              background-color="#86807D"
              color="brown"
              v-model="search"
              append-icon="mdi-magnify"
              label="Search by Name or Description"
              outlined
              rounded
            ></v-text-field>
          </v-flex>
          <v-flex md4>
            <v-select
              background-color="#86807D"
              color="brown"
              v-model="selectedCategory"
              :items="categories"
              label="Filter by category"
              outlined
            >
            </v-select>
          </v-flex>
          <v-flex md12>
            <v-data-table
              :headers="headers"
              :items="filteredList"
              :items-per-page="5"
              class="elevation-5 brown--text"
            ></v-data-table>
          </v-flex>
        </v-layout>
      </v-card>
    </v-container>
  </div>
</template>

<script>
import data from "./data.json";
export default {
  name: "Home",
  components: {},
  data() {
    return {
      search: "",
      selectedCategory: "",
      headers: [
        { text: "Code", value: "itemCode" },
        { text: "Name", value: "itemName" },
        { text: "Description", value: "itemDescription" },
        { text: "Category", value: "itemCategory" }
      ],
      itemsList: data.items,
      categories: ["All", "Books", "Magazines", "Newspapers", "Others"]
    };
  },
  computed: {
    filteredList() {
      if (this.search !== "" && this.selectedCategory === "") {
        return this.itemsList.filter(
          item =>
            item.itemName === this.search ||
            item.itemDescription === this.search
        );
      } else if (this.search === "" && this.selectedCategory !== "") {
        if (this.selectedCategory === "All") {
          return this.itemsList;
        }
        return this.itemsList.filter(
          item => item.itemCategory === this.selectedCategory
        );
      } else if (this.search !== "" && this.selectedCategory !== "") {
        if (this.selectedCategory === "All") {
          return this.itemsList.filter(
            item =>
              item.itemName === this.search ||
              item.itemDescription === this.search
          );
        }
        return this.itemsList.filter(
          item =>
            item.itemCategory === this.selectedCategory &&
            (item.itemName === this.search ||
              item.itemDescription === this.search)
        );
      }
      return this.itemsList;
    }
  }
};
</script>
<style scoped></style>
