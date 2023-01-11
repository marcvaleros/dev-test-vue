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
                      :key="item.id"
                    >
                      <td class="pa-4">
                        <v-text-field
                        dense
                        outlined
                        hide-details
                        label="Product name"
                        v-model="item.name"
                        color="grey darken-1"
                        type="text"
                        ></v-text-field>

                      </td>

                      <td class="pa-4"><v-text-field
                        type="number"
                        dense
                        label="Dollar amount"
                        outlined
                        hide-details
                        v-model="item.amount"
                        color="grey darken-1"
                        ></v-text-field></td>
                      
                      <td class="pa-4">
                        <v-select
                          dense
                          hide-details
                          :items="items"
                          v-model="item.owner"
                          outlined
                          color="grey darken-1"
                          label="Select job owner"
                        ></v-select>
                      </td>


                      <td><v-icon color="black" @click="deleteRow(item)"> 
                         mdi-delete 
                        </v-icon>
                      </td>

                    </tr>
                  </tbody>
                </template>
              </v-simple-table>

          </v-card>
         
          <div class="d-flex justify-space-between ">
            <v-btn text class="blue--text" @click="addRow">
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
        items: [
          {
            text: 'Alice0',
          },
          {
            text: 'Alice1',
          },
          {
            text: 'Alice2',
          },
          {
            text: 'Alice3',
          },
          {
            text: 'Alice4',
          },
         
        ],
        jobs: [{
          id: 1,
          name: 'sample',
          amount: null,
          owner: '',
        }
        ],
      }
    },
    methods: {
      deleteRow(item){
          let index = this.jobs.indexOf(item);
          this.jobs.splice(index,1)
      },
      addRow(){
        let newJob = {
          id:this.jobs.length+1,
          name: '',
          amount: null,
          owner:''
        } 
        this.jobs.push(newJob);
      }
    }
  }
</script>

<style lang="scss">  
  tbody {
     tr:hover {
        background-color: transparent !important;
     }
  };


</style>