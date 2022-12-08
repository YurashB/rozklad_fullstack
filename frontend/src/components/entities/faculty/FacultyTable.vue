<template>
  <v-card elevation="0">
    <v-card-title>
      <h1>Faculties</h1>
    </v-card-title>
    <v-card-text>
      <vue-good-table
          ref="table"
          :columns="columns"
          :rows="rows"
          :select-options="{ enabled: true }"
          :search-options="{ enabled: true }"
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
  name: "FacultyTable",
  data() {
    return {
      columns: [
        {
          label: 'Name',
          field: 'name',
        },
        {
          label: 'Short name',
          field: 'short_name',
          type: 'number',
        },
      ],
      rows: [
        {id: 1, name: 'Faculty of Informatics and Computer Science', short_name: "FICT",},
        {id: 2, name: "Radioengineering Faculty", short_name: "RTF"},
        {id: 3, name: "Faculty of Linguistics", short_name: "FL"},
      ],
    }
  },
  methods: {
    deleteItem() {

    },
    changeItem() {
      let selected = this.$refs['table'].selectedRows[0];
      let id = selected.id;
      let name = selected.name;
      let short_name = selected.short_name;

      this.$router.push({
        name: "updateFaculty",
        params: {id: id},
        query: {id: id, name: name, short_name: short_name},
      })

    }
  }
}
</script>

<style scoped>
</style>