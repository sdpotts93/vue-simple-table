<template>
  <v-app>
    <v-content>
      <SimpleTable />
    </v-content>
  </v-app>
</template>

<script>
import SimpleTable from './components/SimpleTable';

export default {
  name: 'App',
  components: {
    SimpleTable,
  },
  data: () => ({
    //
  }),
};
</script>
