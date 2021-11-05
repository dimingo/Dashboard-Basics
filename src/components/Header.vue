<template>

    <v-app-bar app
      fixed
      color="white"
      elevate-on-scroll
      
        elevation="4"
    >
  

      <v-toolbar-title>Title</v-toolbar-title>
       <v-app-bar-nav-icon @click="$emit('handleDrawer')"></v-app-bar-nav-icon>

      <v-spacer></v-spacer>
   <v-col lg="6" cols="12">
         <v-form class="mt-5" >
             <v-text-field rounded outlined dense append-icon="mdi-magnify" placeholder="Search"></v-text-field>
         </v-form>
     </v-col>
     
    
      <v-btn icon>
        <v-icon>mdi-heart</v-icon>
      </v-btn>

      <v-btn icon>
        <v-icon>mdi-dots-vertical</v-icon>
      </v-btn>
    </v-app-bar>
</template>
<script>
export default {
    setup() {
        
    },
}
</script>
<style scoped>

</style>