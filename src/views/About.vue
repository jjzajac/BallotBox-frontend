<template>
  <suspense>
    <Projects />
  </suspense>
</template>

<script>
import Projects from '../components/Projects.vue';

export default {
  name: 'Subjects',
  components: {
    Projects,
  },
  setup() {},
};
</script>

<style scoped></style>
