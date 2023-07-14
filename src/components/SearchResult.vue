<template>

    <!-- <div class="q-ma-md" style="width: 720px; margin: 0 auto;">
        <q-scroll-area style="height: 100px;">
            <div v-for="n in 100" :key="n" id="div" class="q-py-xs" >
                <div class="contents">
                    <div style="width: 105px;">
                        <q-btn outline dense size="md" class="fa-14 q-px-sm" color="primary" style="width: 100px;">
                            <div class="text-black">教室</div>
                        </q-btn>
                    </div>
                    <div style="width: 300px;">
                        <q-btn outline dense size="md" class="fa-14 q-px-sm" color="primary" style="width: 300px;">
                            <div class="text-black">詳細</div>
                        </q-btn>
                    </div>
                </div>
            </div>
        </q-scroll-area>
    </div> -->




    <div class="q-pa-md" style="width: 720px; margin: 0 auto;">
      <q-scroll-area style="height: 200px;">
        <q-table
        :grid="$q.screen.xs"
        flat bordered

        :rows="rows"
        :columns="columns"
        row-key="name"
        :filter="filter"
        hide-header
      >
      <!-- <template v-slot:top-right>
        <q-input borderless dense debounce="300" v-model="filter" placeholder="Search">
          <template v-slot:append>
            <q-icon name="search" />
          </template>
        </q-input>
      </template> -->
    </q-table>
    </q-scroll-area>
  </div>
  </template>


<script>
import { ref, watch } from 'vue'

const columns = [
  {
    name: 'desc',
    required: true,
    label: 'Dessert (100g serving)',
    align: 'left',
    field: row => row.name,
    format: val => `${val}`,
    sortable: true
  },
  { name: 'calories', align: 'center', label: 'Calories', field: 'calories', sortable: true },
  { name: 'fat', label: 'Fat (g)', field: 'fat', sortable: true },
  { name: 'carbs', label: 'Carbs (g)', field: 'carbs' }
]

const rows = [
  {
    name: 'Frozen Yogurt',
    calories: 159,
    fat: 6.0,
    carbs: 24
  },
  {
    name: 'Ice cream sandwich',
    calories: 237,
    fat: 9.0,
    carbs: 37
  },
  {
    name: 'Eclair',
    calories: 262,
    fat: 16.0,
    carbs: 23
  },
  {
    name: 'Cupcake',
    calories: 305,
    fat: 3.7,
    carbs: 67
  },
  {
    name: 'Gingerbread',
    calories: 356,
    fat: 16.0,
    carbs: 49
  },
  {
    name: 'Jelly bean',
    calories: 375,
    fat: 0.0,
    carbs: 94
  },
  {
    name: 'Lollipop',
    calories: 392,
    fat: 0.2,
    carbs: 98
  },
  {
    name: 'Honeycomb',
    calories: 408,
    fat: 3.2,
    carbs: 87
  },
  {
    name: 'Donut',
    calories: 452,
    fat: 25.0,
    carbs: 51
  },
  {
    name: 'KitKat',
    calories: 518,
    fat: 26.0,
    carbs: 65
  }
]

export default {
  props: {
    filter: {
      type: String,
      required: true
    }
  },

  setup(props) {
  return {
    columns,
    rows
  };
},
}
</script>

<style>
#div {
    display: flex;
    justify-content: center;
    background-color: rgba(105, 206, 155, 0.265);
}

.contents {
    text-align: left;
    height: 29px;
    display: flex;
    flex-direction: row;
}
</style>