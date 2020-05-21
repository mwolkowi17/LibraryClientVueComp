<template>
  <v-app id="inspire">
    <!--<v-navigation-drawer
      v-model="drawer"
      app
      clipped
    >
      <v-list dense>
        <v-list-item link>
          <v-list-item-action>
            <v-icon>mdi-view-dashboard</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title>Dashboard</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        <v-list-item link>
          <v-list-item-action>
            <v-icon>mdi-settings</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title>Settings</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>-->

    <v-app-bar app clipped-left>
      <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
      <v-toolbar-title>Application</v-toolbar-title>
    </v-app-bar>

    <v-content>
      <v-container class="fill-height" fluid>
        <v-row align="center" justify="center">
          <v-col>
            <v-row>
              <v-col>
                <ListOne v-bind:books="books"></ListOne>
              </v-col>
            </v-row>
            <v-row>
              <v-col>
                <FormRent v-on:setemicfuncC="rentBookMeth"></FormRent>
              </v-col>
            </v-row>
          </v-col>
          <v-col>
            <v-row>
              <v-col>
                <ListTwo v-bind:readers="readers"></ListTwo>
              </v-col>
            </v-row>
            <v-row>
              <v-col>
                <FormReturn v-on:setemicfuncD="returnBookMeth"></FormReturn>
              </v-col>
            </v-row>
          </v-col>
          <v-col>
            <v-row>
              <v-col>
                <FormOne   v-on:setemicfuncA="addBookMeth"></FormOne>
              </v-col>
            </v-row>
            <v-row>
              <v-col>
                <FormTwo v-on:setemicfuncB="addReaderMeth"></FormTwo>
              </v-col>
            </v-row>
          </v-col>
        </v-row>
      </v-container>
    </v-content>

    <v-footer app>
      <span>&copy; 2020</span>
    </v-footer>
  </v-app>
</template>

<script>
import ListOne from "@/components/ListOne";
import ListTwo from "@/components/ListTwo";
import FormOne from "@/components/FormOne";
import FormTwo from "@/components/FormTwo";
import FormRent from "@/components/FormRent";
import FormReturn from '@/components/FormReturn';
import axios from "axios";
export default {
  name: "Title",
  components: {
    ListOne,
    ListTwo,
    FormOne,
    FormTwo,
    FormRent,
    FormReturn
  },
  props: {
    source: String
  },
  data: () => ({
    drawer: null,
    books: "",
    readers: "",
    roboczabook:""
  }),
  created() {
    this.$vuetify.theme.dark = true;
    axios
      .get("https://localhost:44381/api/BookCs")
      .then(res => (this.books = res.data));
    axios
      .get("https://localhost:44381/api/Readers")
      .then(res => (this.readers = res.data));
  },
  methods: {
    updateB: function () {
      axios
        .get("https://localhost:44381/api/BookCs")
        .then(res => (this.books = res.data));
        this.$forceUpdate();
    },
    baz: function(x,y){
        console.log('call!'+x+y);
    },
    addBookMeth: function addbook(x,y) {
      const newtitle={
         titleC: x,
        authorC: y,
        rented: false,
        rentedbyReader: 0,
        rentData: "0001-01-01T00:00:00",
        dropOfData: "0001-01-01T00:00:00",
        aliasofReader: null
      }
      axios.post("https://localhost:44381/api/BookCs", newtitle );
      
      const newtitletolist={
        bookCID:this.books[this.books.length-1].bookCID+1,
        titleC: x,
        authorC: y,
        rented: false,
        rentedbyReader: 0,
        rentData: "0001-01-01T00:00:00",
        dropOfData: "0001-01-01T00:00:00",
        aliasofReader: null
      
      }
      this.books.push(newtitletolist);
    },
    addReaderMeth:function addreadermeth(x,y){
      console.log( "bing!" + x +y );
      const newreader={
        
        name: x,
        surname: y,
        books: null,
        alias: "Ewa Danielska"
      }
       axios.post("https://localhost:44381/api/Readers", newreader);
       const newreadertolist={
        readerID:this.readers[this.readers.length-1].readerID+1,
        name: x,
        surname: y,
        books: null,
        alias: "Ewa Danielska"
       }
       this.readers.push(newreadertolist);
    },
    rentBookMeth:function rentbookmeth(x,y){
       console.log("clicrent!",x,y)
        for(var m=0; m < this.books.length; m++){
        //let i;
        // console.log("trafiony")
        // console.log(this.books[m].titleC)
        // console.log(x)
        if(this.books[m].titleC===x){
       this.roboczabook=this.books[m];
       console.log("trafiony")
       this.roboczabook.rented=true;
       var Readerint=parseInt(y)
       this.roboczabook.rentedbyReader=Readerint;

        }
    }
    const num=this.roboczabook.bookCID;
    axios.put("https://localhost:44381/api/BookCs/"+num,this.roboczabook);
    },
    returnBookMeth: function returnbookmeth(x){
     console.log("bang!"+x)

     for(var m=0; m < this.books.length; m++)
     {
        //let i;
        // console.log("trafiony")
        // console.log(this.books[m].titleC)
        // console.log(this.bookIDSource)
        if(this.books[m].titleC===x)
        {
       this.roboczabook=this.books[m];
       console.log("trafiony")
       this.roboczabook.rented=false;
      
       this.roboczabook.rentedbyReader=0;
        }
    }
     var num=this.roboczabook.bookCID;
      axios.put("https://localhost:44381/api/BookCs/"+num,this.roboczabook);
    }
  },
  
};
</script>