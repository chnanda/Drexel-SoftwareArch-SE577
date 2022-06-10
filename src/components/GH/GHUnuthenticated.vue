<template>
  <q-card
    flat
    class="my-card"
    :class="hasBeenSolved ? 'bg-green-1' : 'bg-red-1'"
  >
    <q-card-section>
      <div class="text-h6">UnAuthenticated</div>
      <!-- Form Goes Here -->
      <q-form @submit="onSubmit" @reset="onReset" class="q-gutter-md">
        <div class="text-h8 text-left">
          Execution Time: <strong>{{ executionTime }}</strong> ms
        </div>
        <div class="text-h8 text-left">
          <strong> GH Api Response: </strong>
        </div>
        <div class="text-h8 text-left">
          {{ apiResponse }}
        </div>
        <q-input v-model="solverURL" label="SolverURL" />
        <div>
          <q-btn label="UnAuthenticated" type="submit" color="primary" />
        </div>
      </q-form>
    </q-card-section>
  </q-card>
</template>

<script lang="ts">
export default {
  name: 'UnauthenticatedComponent',
};
</script>

<script setup lang="ts">
//NOTICE THE SETUP IN THE SCRIPT TAG, MAKES THINGS EASIER

import { ref, onMounted } from 'vue';
//import { v4 as uuidv4 } from 'uuid';
import axios from 'axios';
//import sha256 from 'crypto-js/sha256';

let apiResponse = ref('');
let executionTime = ref(0);
let solverURL = ref('');

const onReset = () => {
  apiResponse.value = '';
  executionTime.value = 0;
  solverURL.value = 'http://localhost:9094/gh/users/chnanda';
};

const onSubmit = async () => {
  const result = await axios.get(solverURL.value, {});

  if (result.status === 200) {
    //notice that there is no automatic type checking here given data is
    //any, if you use generics, like in the advanced component, you will
    //see the difference
    apiResponse.value = result.data;
  }
};

onMounted(() => onReset());
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
