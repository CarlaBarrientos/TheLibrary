<template>
  <div class="home">
    <h1>Home page</h1>
  </div>
</template>

<script>
export default {
  name: "Home",
  components: {},
  data() {
    return {
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
      ]
    };
  }
};
</script>
