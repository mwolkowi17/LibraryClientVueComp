<template>
     <v-card class="mx-auto" outlined>
    <v-list-item three-line>
      <v-list-item-content>
        <div class="overline mb-4">OVERLINE</div>
        <v-list-item-title class="headline mb-1">Add Reader</v-list-item-title>
        <v-col>
          <v-row>
            <v-col>
              <v-text-field  v-model="nameSource" label="title"></v-text-field>
            </v-col>
          </v-row>
          <v-row>
            <v-col>
              <v-text-field  v-model="surnameSource" label="author"></v-text-field>
            </v-col>
          </v-row>
        </v-col>
      </v-list-item-content>
    </v-list-item>

    <v-card-actions>
      <v-btn text v-on:click="emitFuncTwo">Add Reader</v-btn>
    </v-card-actions>
  </v-card>
</template>
<script>

export default {
    name: "FormTwo",
    data(){
        return{
          nameSource:"",
          surnameSource:""  
        }
    },
    methods: {
        emitFuncTwo: function emitfunctwo(){
            this.$emit("setemicfuncB", this.nameSource, this.surnameSource)
        }

    }
}
</script>