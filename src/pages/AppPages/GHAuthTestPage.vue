<template>
  <div class="q-pa-md">
    <q-banner class="bg-primary text-white">
      <h6>GitHub Auth test</h6>
    </q-banner>
    <div class="row">
      <div class="col-4">
        <AuthenticatedComponent />
      </div>
      <div class="col-4">
        <UnauthenticatedComponent />
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import AuthenticatedComponent from 'src/components/GH/GHAuthenticated.vue';
import UnauthenticatedComponent from 'src/components/GH/GHUnuthenticated.vue';

export default defineComponent({
  name: 'BCPage',
  components: { AuthenticatedComponent, UnauthenticatedComponent },
  setup() {
    return {};
  },
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
