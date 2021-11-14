<template>
  <v-app id="inspire">
  
    <Header @handleDrawer="drawer =! drawer"/>
    <Sidebar :drawer='drawer'/>
   <v-content>
   <router-view/>
   </v-content>
  </v-app>
</template>

<script>
import Header from './components/Header.vue';
import Sidebar from './components/Sidebar.vue';
export default {
  components: { Sidebar, Header },
  data: () => ({
    cards: ["Today", "Yesterday"],
    drawer: false,
    
  }),
};
</script>
