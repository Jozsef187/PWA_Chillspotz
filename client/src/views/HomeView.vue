<script setup>
import { useSpotzStore } from '../stores/spotzStore';
import { ref } from 'vue';

const showdetailpage = ref(false);
console.log(showdetailpage);
const store = useSpotzStore();
store.getSpotz();

const cols = [
  { name: 'name', field: 'titel', label: 'Name', align: 'left' },
  { name: 'rating', field: 'rating', label: 'Rating', align: 'right' },
  { name: 'likes', field: 'likes', label: 'Likes', align: 'left' },
  { name: 'actions', label: 'Actions', align: 'Center' },
];
</script>

<template>
  <div class="q-mt-md q-ml-sm q-mr-sm">
    <q-card>
      <q-table
        grid
        title="Chillspotz:"
        :rows="store.data"
        :columns="cols"
        row-key="name"
        :pagination="{ rowsPerPage: 10 }"
        class="lt-sm"
      >
        <template v-slot:body-cell-actions="props">
          <q-td :props="props">
            <q-btn label="Action">Edit:</q-btn>
          </q-td>
        </template>
      </q-table>
    </q-card>
    <q-card>
      <q-table
        title="Spotz to chill out:"
        :rows="store.data"
        :columns="cols"
        row-key="name"
        :pagination="{ rowsPerPage: 10 }"
        class="gt-xs"
      >
      </q-table>
    </q-card>
  </div>
</template>

<style lang="css" scoped></style>
