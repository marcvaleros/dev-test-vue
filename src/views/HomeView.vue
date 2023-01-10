<template>
  <v-container grid-list-xl>
    <h1 class="title">Project</h1>
    <v-stepper v-model="e1">
      <v-stepper-header>
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

      <v-stepper-items>
        <v-stepper-content  step="1">
          <v-card
            class="mb-12"
            color="grey lighten-1"
            height="200px"
          ></v-card>

          <v-btn
            color="primary rounded-pill"
            @click="e1 = 2"
          >
            NEXT
          </v-btn>

          <v-btn text class="blue--text">
            + ADD ROW
          </v-btn>
        </v-stepper-content>

        <v-stepper-content step="2">
          <v-card
            class="mb-12"
            color="grey lighten-1"
            height="200px"
          ></v-card>
          <v-btn text class="blue--text" @click="e1 = 1">
             BACK
          </v-btn>
        </v-stepper-content>
      </v-stepper-items>
    </v-stepper>
  </v-container>
</template>

<script>
  import HelloWorld from '../components/HelloWorld'
  /* eslint-disable */
  export default {
    name: 'Home',
    components: {
      HelloWorld,
    },
    data() {
      return {
        e1: 1,
      }
    },
  }
</script>
