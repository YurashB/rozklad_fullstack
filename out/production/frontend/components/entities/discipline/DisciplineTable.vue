<template>
  <v-card elevation="0">
    <v-card-title>
      <h1>Disciplines</h1>
    </v-card-title>
    <v-card-text>
      <vue-good-table
          :columns="columns"
          :rows="rows"
          :select-options="{ enabled: true }"
          :search-options="{ enabled: true }"
          ref="table"
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
  name: "DisciplineTable",
  data() {
    return {
      columns: [
        {
          label: 'Name',
          field: 'name',
        },
      ],
      rows: [
        {id: 1, name: "English"},
        {id: 2, name: "Web development"},
        {id: 3, name: "OS"},
        {id: 4, name: "Front-end"},
        {id: 5, name: "Math"},
      ],
    }
  },
  methods: {
    deleteItem(){

    },
    changeItem() {
      let selected = this.$refs['table'].selectedRows[0];
      let id = selected.id;
      let name = selected.name;

      this.$router.push({
        name: "updateDiscipline",
        params: {id: id},
        query: {id: id, name: name},
      })
    }
  }
}
</script>

<style scoped>

</style>