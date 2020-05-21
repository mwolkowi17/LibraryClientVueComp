<template>
     <v-card class="mx-auto" outlined>
              <v-list-item three-line>
                <v-list-item-content>
                  <div class="overline mb-4">OVERLINE</div>
                  <v-list-item-title class="headline mb-1">Readers</v-list-item-title>
                  <v-simple-table height="260px">
                    <template v-slot:default>
                      <thead>
                        <tr>
                          <th class="text-left">ID</th>
                          <th class="text-left">Name</th>
                          <th class="text-left">Surname</th>
                        </tr>
                      </thead>
                      <tbody>
                        <tr v-for="(item,keyb) in readers" v-bind:key="keyb">
                          <td>{{ item.readerID }}</td>
                          <td>{{ item.name }}</td>
                          <td>{{ item.surname }}</td>
                        </tr>
                      </tbody>
                    </template>
                  </v-simple-table>
                </v-list-item-content>
              </v-list-item>

              <v-card-actions></v-card-actions>
            </v-card>
</template>

<script>
export default {
    name:"ListTwo",
    props:["readers"]
}
</script>