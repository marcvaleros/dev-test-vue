<template>
  <v-container>
    <h1 class="text-h5 mb-2 font-weight-bold elevation-0">Project</h1>
    <v-stepper v-model="e1" class="elevation-0">
      <v-stepper-header  class="elevation-4">
        <v-stepper-step
          :complete="e1 > 1"
          step="1"
        >
          Configuration
        </v-stepper-step>

        <v-divider></v-divider>

        <v-stepper-step
          :complete="e1 > 2"
          step="2"
        >
          Summary
        </v-stepper-step>
      </v-stepper-header>

      <v-stepper-items class="mt-1">
        <v-stepper-content step="1" class="grey lighten-2" >
          <v-card
            class="mb-12 elevation-0 grey lighten-2" 
            >

            <v-simple-table class="grey lighten-2">
                <template v-slot:default>
                  <thead>
                    <tr>
                      <th class="text-left">
                        Add plan name
                      </th>
                      <th class="text-left">
                        $ Amount
                      </th>
                      <th class="text-left">
                        Select job owner
                      </th>
                      <th class="text-left">
                      </th>
                    </tr>
                  </thead>

                  <tbody>
                    <tr v-for="item in jobs"
                      :key="item.name"
                    >
                      <td class="pa-4">
                        <v-text-field
                        dense
                        label="Product name"
                        outlined
                        hide-details
                        :placeholder="item.name"
                        :value="item.name"
                        color="grey darken-1"
                        ></v-text-field>
                      </td>

                      <td class="pa-4"><v-text-field
                        dense
                        label="Dollar amount"
                        outlined
                        hide-details
                        :placeholder="item.amount"
                        :value="item.amount"
                        color="grey darken-1"
                        ></v-text-field></td>
                      
                      <td class="pa-4">
                        <!-- <v-text-field
                        dense
                        label="Select job owner"
                        outlined
                       
                        :placeholder="item.owner"
                        :value="item.owner"
                        color="grey darken-1"
                        ></v-text-field> -->

                        <v-select
                          dense
                          hide-details
                          :items="items"
                          :key="items.name"
                          label="Select job owner"
                          outlined
                        ></v-select>


                      </td>


                      <td>Delete</td>
                    </tr>
                  </tbody>
                </template>
              </v-simple-table>

          </v-card>
         
          <div class="d-flex justify-space-between ">
            <v-btn text class="blue--text">
              + ADD ROW
            </v-btn>
            
            <v-btn
              color="primary rounded-pill"
              @click="e1 = 2"
            >
              NEXT
            </v-btn>
          </div>

        </v-stepper-content>

        <v-stepper-content step="2" class="grey lighten-2" >
          <v-card
            class="mb-12 elevation-0 grey lighten-2"
            height="200px"
          ></v-card>

          <v-btn text class="blue--text" @click="e1 = 1">
            &lt; BACK
          </v-btn>
        </v-stepper-content>
      </v-stepper-items>
    </v-stepper>
  </v-container>
</template>

<script>
  /* eslint-disable */

  export default {
    name: 'Home',
    components: {
    },
    data() {
      return {
        e1:1,
        items: 
          {
            name: 'Alice0',
            name: 'Alice1',
            name: 'Alice2',
            name: 'Alice3',
            name: 'Alice4',
            
          }
        ,
        jobs: [
          {
            name: 'Eclair',
            amount: 262,
            owner: 'Unknown',
          },
          {
            name: 'Cupcake',
            amount: 305,
            owner: 'Unknown',
          },
          {
            name: 'Gingerbread',
            amount: 356,
            owner: 'Unknown',
          },
          {
            name: 'Jelly bean',
            amount: 375,
            owner: 'Unknown',
          },
        ],
      }
    },
  }
</script>

<style lang="scss">  
  tbody {
     tr:hover {
        background-color: transparent !important;
     }
  };


</style>