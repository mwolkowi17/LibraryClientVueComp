<template>
    <v-card class="mx-auto" outlined>
                  <v-list-item three-line>
                    <v-list-item-content>
                      <div class="overline mb-4">OVERLINE</div>
                      <v-list-item-title class="headline mb-1">Books</v-list-item-title>
                      <v-simple-table height="260px">
                        <template v-slot:default>
                          <thead>
                            <tr>
                              <th class="text-left">ID</th>
                              <th class="text-left">Title</th>
                              <th class="text-left">Author</th>
                              <th class="text-left">Rented</th>
                              <th class="text-left">Reader</th>
                            </tr>
                          </thead>
                          <tbody>
                            <tr v-for="(item,keyb) in books" v-bind:key="keyb">
                              <td>{{ item.bookCID }}</td>
                              <td>{{ item.titleC }}</td>
                              <td>{{ item.authorC }}</td>
                              <td>{{ item.rented}}</td>
                              <td>{{ item.rentedbyReader}}</td>
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
    name: "ListOne",
    data(){
        return{

        }
    },
    props:['books']
}
</script>