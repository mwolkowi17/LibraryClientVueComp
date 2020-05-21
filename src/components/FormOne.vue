<template>
  <v-card class="mx-auto" outlined>
    <v-list-item three-line >
      <v-list-item-content>
        <div class="overline mb-4">OVERLINE</div>
        <v-list-item-title class="headline mb-1">Add Book</v-list-item-title>
        <v-col>
          <v-row>
            <v-col>
              <v-text-field  v-model="titleSource" label="title"></v-text-field>
            </v-col>
          </v-row>
          <v-row>
            <v-col>
              <v-text-field  v-model="authorSource" label="author"></v-text-field>
            </v-col>
          </v-row>
        </v-col>
      </v-list-item-content>
    </v-list-item>

    <v-card-actions>
      <v-btn text v-on:click="emitFunc">Add Book</v-btn>
    </v-card-actions>
  </v-card>
</template>

<script>
import axios from "axios";
export default {
  name: "FormOne",
  data() {
    return {
      titleSource: "",
      authorSource: ""
    };
  },
  methods: {
    addBookMeth: function addbook() {
      axios.post("https://localhost:44381/api/BookCs", {
        titleC: this.titleSource,
        authorC: this.authorSource,
        rented: false,
        rentedbyReader: 0,
        rentData: "0001-01-01T00:00:00",
        dropOfData: "0001-01-01T00:00:00",
        aliasofReader: null
      });
      //this.$forceUpdate();
      //this.$parent.baz();

      /*axios
        .get("https://localhost:44381/api/BookCs")
        .then(res => (this.books = res.data));
      */
      //this.$emit("")
    },
    emitFunc: function emitfunc() {
      this.$emit("setemicfuncA", this.titleSource, this.authorSource);
    },
    doo: function dosomethig() {
      console.log("signal!");
    }
  }
};
</script>