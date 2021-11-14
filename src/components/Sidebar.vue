<template>
  <v-navigation-drawer v-model="drawer" app>
    <v-sheet color="blue lighten-4" class="pa-4">
      <div class="text-center">
      <v-avatar class="mb-4" color="grey darken-1" size="64"></v-avatar>

      <div>ketcha@gmail.com</div>
      </div>
    </v-sheet>

    <v-divider></v-divider>

    <v-list>
      <v-list-item v-for=" link in links" :key="link.text" router :to="link.route">
        <v-list-item-icon>
          <v-icon>{{ link.icon }}</v-icon>
        </v-list-item-icon>

        <v-list-item-content>
          <v-list-item-title>{{ link.title }}</v-list-item-title>
        </v-list-item-content>
      </v-list-item>
    </v-list>
  </v-navigation-drawer>
</template>
<script>
export default {
  props: ["drawer"],
  name: "sidebar",
  data() {
    return {
      links: [    
         { title: "Dashboard", icon: "mdi-folder", route: "#" },
       { title: "Profile", icon: "mdi-folder", route: "#" },
         { title: "Folders", icon: "mdi-folder", route: "/allfolders" },
      ],
    };
  },
};
</script>
<style scoped></style>
