<template>
  <v-app >
    <v-container>
      
        <v-row no-gutters >
          <v-col :cols="2" class="mr-1 flex-grow-1">
            <v-card    >
              <v-card-title> Folder List </v-card-title>
              <v-card-text>
                <v-treeview
                  v-model="tree"
                  :items="items.data"
                  activatable
                  item-key="name"
                  open-on-click
                 
                 
                >
                  <template slot="prepend" slot-scope="{ item, open }" >
                    <v-icon v-if="item.uuid" @click="test(item)">
                      {{ open ? "mdi-folder-open" : "mdi-folder" }}
                    </v-icon>
                  </template>
                </v-treeview>
              </v-card-text>
            </v-card>
          </v-col>
          <v-col :cols="9" class="flex-grow-1">
           
              
                
                  <template>
                    <v-card width="800">
                      <v-card-title>
                        Dcouments
                       
                        <v-spacer></v-spacer>
                        <v-text-field
                          v-model="search"
                          append-icon="mdi-magnify"
                          label="Search"
                          single-line
                          hide-details
                        ></v-text-field>
                      </v-card-title>
                      <v-data-table
                        :headers="headers"
                        :items="data"
                        :search="search"
                        :v-model="data"
                      ></v-data-table>
                     
                    </v-card>
                  </template>
                
           
          
          </v-col>
        </v-row>
  
    </v-container>
  </v-app>
</template>
<script>

import axios from "axios";
export default {
  
  data() {
    return {
       search: '',
        headers: [
          {
            text: 'Title',
            align: 'start',
            sortable: false,
            value: 'title' ,
          },
          { text: 'Path', value: 'uuid' },
          { text: 'Author ', value: 'author' },
          { text: 'Is Convertable to Pdf ', value: 'isConvertibleToPdf' },
          { text: 'Is locked ', value: 'isLocked' },
          { text: 'Type ', value: 'type' },


        ],
        
      
      files: {
        html: "mdi-language-html5",
        js: "mdi-nodejs",
        json: "mdi-code-json",
        md: "mdi-language-markdown",
        pdf: "mdi-file-pdf",
        png: "mdi-file-image",
        txt: "mdi-file-document-outline",
        xls: "mdi-file-excel",
      },
      tree: [],
      items: [],
      documents: [],
      data:[]
    };
  },
  mounted() {
    this.loadtree();
   
  },

  methods: {
    async loadtree() {
      axios
        .get("http://127.0.0.1:8000/api/get-folders")
        .then((response) => {
          this.items = response.data;
        })
        .catch((error) => {
          console.log(error);
          this.errored = true;
        })
        .finally(() => (this.loading = false));
    },
    listDocument: function (item) {
      let name = item.name;
      console.log(name);
    },
   test(item) {
     
      axios
        .get("http://127.0.0.1:8000/api/get-document-children/"+item.uuid )

        .then((response) => {
          this.documents = response.data;
          this.data = this.documents.data;
          console.log(this.data);
          
         
        })
        .catch((error) => {
          console.log(error);
          this.errored = true;
        })
        .finally(() => (this.loading = false));
    },
  },
};
</script>
