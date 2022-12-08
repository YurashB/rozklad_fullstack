<template>
  <v-card elevation="1" width="40%" class="mx-auto m-p ">
    <v-card-title>
      <h2>Result</h2>
    </v-card-title>
    <v-card-text>
      {{result}}
    </v-card-text>
  </v-card>
</template>

<script>
export default {
  data() {
    return {
      result: this.$route.query
    }
  },
}
</script>
