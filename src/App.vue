<template>
  <q-layout view="hHh lpR fFf">

    <q-header id="hoge" elevated class="text-white" style="background-color: #009999;" height-hint="98">
      <q-toolbar style="background-color: rgba(127, 255, 212, 0); max-width: fit-content;">

        <q-btn round dense flat icon="menu" class="q-mr-xs">
          <q-menu transition-show="flip-right" transition-hide="flip-left">
            <q-list style="min-width: 100px">
              <div class="MENU">
                <q-item clickable>
                  <q-item-section>🕒履歴</q-item-section>
                </q-item>
                <q-item clickable>
                  <q-item-section>📗ブックマーク</q-item-section>
                </q-item>
                <q-separator />
                <q-item clickable>
                  <q-item-section>🔩設定</q-item-section>
                </q-item>
              </div>
            </q-list>
          </q-menu>
        </q-btn>

        <q-toolbar-title>
          <q-avatar>
            <img src="./assets/image/uoa-icon.jpg">
          </q-avatar>
          UoA MAP
        </q-toolbar-title>


      </q-toolbar>

      <q-tabs class="absolute-center" style="background-color: rgba(240, 255, 255, 0); width: 600px;">
        <div class="q-pa-md">
          <div class="q-gutter-y-md column" style="width: 400px; max-width: 100%">
            <q-toolbar class="text-white rounded-borders justify-center">

              <q-input dark dense standout v-model="text" input-class="text-left custom-input-class" class="q-ml-md" style="background-color: #36d0d05c; width: 100%;">
                <template v-slot:append>
                  <q-icon v-if="text === ''" name="search" />
                  <q-icon v-else name="clear" class="cursor-pointer" @click="text = ''" />
                </template>
              </q-input>

            </q-toolbar>
          </div>
        </div>
      </q-tabs>
    </q-header>

    <q-page-container>
      <router-view />
      <SearchResult :filter="text" />
      <Mapping />
    </q-page-container>

  </q-layout>
</template>

<script>
import { ref, watch } from 'vue'
import SearchResult from './components/SearchResult.vue';
import Mapping from './components/Map.vue';

export default {
  setup() {
    const leftDrawerOpen = ref(false);
    const rightDrawerOpen = ref(false);
    const text = ref("");
    const filter = ref("");

    watch(text, (newValue) => {
      filter.value = newValue;
    });

    return {
      text,
      filter,
      leftDrawerOpen,
      toggleLeftDrawer() {
        leftDrawerOpen.value = !leftDrawerOpen.value;
      },
      rightDrawerOpen,
      toggleRightDrawer() {
        rightDrawerOpen.value = !rightDrawerOpen.value;
      }
    };
  },
  components: { SearchResult, Mapping }
}
</script>

<style>
#hoge {
  display: flex;
}
</style>