<template>
  <div class="q-pa-md">
    <AboutSection />
    <LoginSection />
    <InfoSection />
    <ReposListSection />
    <RepoDetailsSection />
    <EndNotesSection />
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import AboutSection from 'components/About/AboutSection.vue';
import LoginSection from 'src/components/About/LoginSection.vue';
import InfoSection from 'src/components/About/InfoSection.vue';
import ReposListSection from 'src/components/About/ReposListSection.vue';
import RepoDetailsSection from 'src/components/About/RepoDetailsSection.vue';
import EndNotesSection from 'components/About/EndNotesSection.vue';

export default defineComponent({
  name: 'AboutModularPage',
  components: {
    AboutSection,
    LoginSection,
    InfoSection,
    ReposListSection,
    RepoDetailsSection,
    EndNotesSection,
  },
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
