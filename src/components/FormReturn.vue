<template>
  <v-card class="mx-auto" outlined>
    <v-list-item three-line>
      <v-list-item-content>
        <div class="overline mb-4">OVERLINE</div>
        <v-list-item-title class="headline mb-1">Return Book</v-list-item-title>
        <v-col>
          <v-row>
            <v-col>
              <v-text-field v-model="returnBookTitle" label="Title"></v-text-field>
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
      <v-btn text v-on:click="emitFuncReturn">Return Book</v-btn>
    </v-card-actions>
  </v-card>
</template>

<script>
export default {
  name: "FormReturn",
  data() {
    return {
      returnBookTitle: "",
      readerIDSource: ""
    };
  },
  methods: {
    emitFuncReturn: function emitfincreturn() {
      this.$emit("setemicfuncD", this.returnBookTitle);
    }
  }
};
</script>