<template>
  <v-card elevation="1" width="40%" class="mx-auto m-p ">
    <v-card-title>
      <h2>{{ headerTitle }}</h2>
    </v-card-title>
    <v-card-text>
      <v-form v-model="valid" lazy-validation ref="form" >
        <v-text-field
            class="text-field-m-p"
            variant="outlined"
            v-model="faculty.name"
            :rules="nameRules"
            label="Name of faculty"
            type="text"
        >
        </v-text-field>
        <v-text-field
            class="text-field-m-p"
            variant="outlined"
            v-model="faculty.short_name"
            :rules="nameRules"
            label="Short name of faculty"
            type="text"
        >
        </v-text-field>
        <v-btn
            v-if="this.$route.query.id"
            width="100%"
            color="green"
            variant="elevated"
            @click="change"
        >Change
        </v-btn>
        <v-btn
            v-if="!this.$route.query.id"
            width="100%"
            type="submit"
            color="green"
            variant="elevated"
            @click="add"
        >Add
        </v-btn>
      </v-form>
    </v-card-text>
  </v-card>
</template>

<script>

export default {
  data() {
    return {
      faculty: {
        id: this.$route.query.id,
        name: this.$route.query.short_name,
        short_name: this.$route.query.name
      },
      valid: false,
      nameRules: [
        v => !!v || 'Name is required',
      ],
      headerTitle: this.$route.query.id ? "Change faculty" : "Add new faculty",
    }
  },
  methods: {
    change() {

    },
    add() {

    }
  }
}
</script>
