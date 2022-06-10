<template>
  <q-card
    flat
    class="my-card"
    :class="hasBeenSolved ? 'bg-green-1' : 'bg-red-1'"
  >
    <q-card-section>
      <div class="text-h6">All Branches</div>
      <!-- Form Goes Here -->
      <q-form @submit="onSubmit" @reset="onReset" class="q-gutter-md">
        <div class="row">
          <q-table
            title="Branches"
            dense
            :rows="brows"
            :columns="columns"
            row-key="id"
          />
        </div>

        <div>
          <q-btn label="Show All Branches" type="submit" color="primary" />
        </div>
      </q-form>
    </q-card-section>
  </q-card>
</template>

<script lang="ts">
export default {
  name: 'AuthenticatedComponent',
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

type branchRow = {
  id: string;
  name: string;
};

const columns = [
  { name: 'id', label: 'ID', align: 'left', field: 'id', sortable: true },
  { name: 'name', label: 'name', align: 'left', field: 'name', sortable: true },
];
let brows = ref([] as branchRow[]);

const onReset = () => {
  apiResponse.value = '';
  executionTime.value = 0;
  solverURL.value =
    'http://localhost:9094/ghsecure/repos/chnanda/Drexel-SoftwareArch-SE577/branches';
};

const onSubmit = async () => {
  const result = await axios.get(solverURL.value, {});

  if (result.status === 200) {
    //notice that there is no automatic type checking here given data is
    //any, if you use generics, like in the advanced component, you will
    //see the difference
    brows.value = [];
    const brList = result.data as branchRow[];
    const bresList = brList.map((row) => {
      const mappedBRow: branchRow = {
        id: row.id,
        name: row.name,
      };
      return mappedBRow;
    });
    console.log('DEBUG', bresList);
    brows.value = bresList;
  }
};

onMounted(() => onReset());
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
