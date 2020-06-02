<template>
  <v-app>
    <v-content class="content">
      <router-view />
    </v-content>
  </v-app>
</template>

<script>
export default {
  name: "App",

  components: {},

  data: () => ({
    //
  })
};
</script>
<style scoped>
.content {
  background-image: url(https://img.freepik.com/foto-gratis/estanteria-borrosa-muchos-libros-antiguos-libreria-o-biblioteca_36051-477.jpg?size=626&ext=jpg);
  background-size: cover;
}
</style>
