<template>
  <v-card elevation="0">
    <v-card-title>
      <h1>Teachers</h1>
    </v-card-title>
    <v-card-text>
      <vue-good-table
          ref="table"
          :columns="columns"
          :rows="rows"
          :select-options="{ enabled: true }"
          :search-options="{ enabled: true }"
          @on-row-click="onRowClick"
      >
        <template #selected-row-actions>
          <v-btn
              v-show="this.$refs['table'].selectedRows.length === 1"
              class="font"
              size="x-small"
              color="green"
              variant="plain"
              @click="changeItem"

          >Change
          </v-btn>
          <v-btn
              class="font"
              size="x-small"
              color="red"
              variant="plain"
              @click="deleteItem"
          >Delete
          </v-btn>
        </template>
      </vue-good-table>
    </v-card-text>
  </v-card>
</template>

<script>
export default {
  name: "TeacherTable",
  data() {
    return {
      columns: [
        {
          label: 'Name',
          field: 'name',
        },
        {
          label: 'Surname',
          field: 'surname',
        },
        {
          label: 'Email',
          field: 'email',
        },
        {
          label: 'Phone',
          field: 'phone',
        },
      ],
      rows: [
        {id: 1, name: "Gisselle", surname: "Turner", email: "аarchibald.fay@gmailll.org", phone: "050-623-6131"},
        {id: 2, name: "Dereck", surname: "Wehner", email: "аshyanne07@gasssmail.com", phone: "035-289-3199"},
        {id: 3, name: "Rollin", surname: "Johnson", email: "аkschulist@dailyladylog.com", phone: "035-289-3199"},
        {id: 4, name: "Gisselle", surname: "Kunze", email: "аgeovanny.tromp@curcuplas.me", phone: "035-289-3199"},
        {id: 5, name: "Toy", surname: "Friesen", email: "аalysa02@dailyladylog.com", phone: "035-289-3199"},
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
  methods: {
    deleteItem(){

    },
    changeItem() {
      let selected = this.$refs['table'].selectedRows[0];
      let id = selected.id;
      let name = selected.name;
      let surname = selected.surname;
      let email = selected.email;
      let phone = selected.phone;

      this.$router.push({
        name: "updateTeacher",
        params: {id: id},
        query: {id: id, name: name, surname: surname, email: email, phone: phone},
      })
    },
  }
}
</script>

<style scoped>

</style>