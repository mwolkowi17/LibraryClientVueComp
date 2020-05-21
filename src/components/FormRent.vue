<template>
  <v-card class="mx-auto" outlined>
    <v-list-item three-line>
      <v-list-item-content>
        <div class="overline mb-4">OVERLINE</div>
        <v-list-item-title class="headline mb-1">Rent Book</v-list-item-title>
        <v-col>
          <v-row>
            <v-col>
              <v-text-field v-model="bookIDSource" label="Title"></v-text-field>
            </v-col>
          </v-row>
          <v-row>
            <v-col>
              <v-text-field v-model="readerIDSource" label="Reader ID"></v-text-field>
            </v-col>
          </v-row>
        </v-col>
      </v-list-item-content>
    </v-list-item>

    <v-card-actions>
      <v-btn text v-on:click="emitFuncRent">Rent Book</v-btn>
    </v-card-actions>
  </v-card>
</template>

<script>
export default {
  name: "FormRent",
  data() {
    return {
      bookIDSource: "",
      readerIDSource: ""
    };
  },
  methods: {
    emitFuncRent: function emitfuncrent() {
      this.$emit("setemicfuncC", this.bookIDSource, this.readerIDSource);
    }
  }
};
</script>