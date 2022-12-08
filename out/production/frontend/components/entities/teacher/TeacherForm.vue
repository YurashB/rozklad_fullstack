<template>
  <v-card elevation="1" width="40%" class="mx-auto m-p ">
    <v-card-title>
      <h2>{{headerTitle}}</h2>
    </v-card-title>
    <v-card-text>
      <v-form v-model="valid" lazy-validation ref="form">
        <v-text-field
            class="text-field-m-p"
            variant="outlined"
            v-model="teacher.name"
            :rules="nameRules"
            label="Name of teacher"
            type="text"
        >
        </v-text-field>
        <v-text-field
            class="text-field-m-p"
            variant="outlined"
            v-model="teacher.surname"
            :rules="nameRules"
            label="Surname of teacher"
            type="text"
        >
        </v-text-field>
        <v-text-field
            class="text-field-m-p"
            variant="outlined"
            v-model="teacher.email"
            :rules="emailRules"
            label="Email of teacher"
            type="email"
        >
        </v-text-field>
        <v-text-field
            class="text-field-m-p"
            variant="outlined"
            v-model="teacher.phone"
            v-mask="'38(0##)###-##-##'"
            placeholder="38(0__)___-__-__"
            :rules="phoneRules"
            label="Phone of teacher"
            type="tel"
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
import {mask} from 'vue-the-mask'

export default {
  data() {
    return {
      valid: false,
      headerTitle: this.$route.query.id ? "Change teacher" : "Add new teacher",
      actionButtonTitle: "Add",
      nameRules: [ v => !!v || 'Name is required',
        v => /^[a-zA-Z]+$/.test(v) || "Only letters are required"],
      emailRules: [
          v => !!v || 'Email is required',
          v => /^[\w-.]+@([\w-]+\.)+[\w-]{2,4}$/.test(v) || " Invalid email entered"
      ],
      phoneRules: [
        v => !!v || 'Phone is required',
          v=> v.length > 15 || "Invalid phone entered"
      ],
      teacher: {
        id: this.$route.query.id,
        name: this.$route.query.name,
        surname: this.$route.query.surname,
        email: this.$route.query.email,
        phone: this.$route.query.phone
      }
    }
  },
  directives: {
    mask
  },
  methods: {
    change() {

    },
    add() {

    }
  }
}
</script>
