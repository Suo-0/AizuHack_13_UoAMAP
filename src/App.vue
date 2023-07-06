<template>
  <q-layout view="hHh lpR fFf">

    <q-header elevated class="bg-primary text-white" height-hint="98">
      <q-toolbar>


        <q-toolbar-title>
          <q-avatar>
            <img src="https://cdn.quasar.dev/logo-v2/svg/logo-mono-white.svg">
          </q-avatar>
          UoA_Aizu_MAP
        </q-toolbar-title>


      </q-toolbar>

      <q-tabs align="left">
        <q-route-tab to="/page1" label="Page One" />
        <q-route-tab to="/page2" label="Page Two" />
        <q-route-tab to="/page3" label="Page Three" />
      </q-tabs>
      <q-tabs>
        <div class="q-pa-md">
          <div class="q-gutter-y-md column" style="width: 300px; max-width: 100%">
            <q-toolbar class="bg-primary text-white rounded-borders justify-center">


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


              <q-input dark dense standout v-model="text" input-class="text-left custom-input-class" class="q-ml-md">
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

    <q-drawer show-if-above v-model="leftDrawerOpen" side="left" bordered>
      <!-- drawer content -->
    </q-drawer>

    <q-drawer show-if-above v-model="rightDrawerOpen" side="right" bordered>
      <!-- drawer content -->
    </q-drawer>

    <q-page-container>
      <router-view />
      <SearchResult/>
      <Mapping/>
    </q-page-container>

    <q-footer elevated class="bg-grey-8 text-white">
      <q-toolbar>
        <q-toolbar-title>
          <q-avatar>
            <img src="https://cdn.quasar.dev/logo-v2/svg/logo-mono-white.svg">
          </q-avatar>
          <div>Title</div>
        </q-toolbar-title>
      </q-toolbar>
    </q-footer>

  </q-layout>
</template>

<script>
import { ref } from 'vue'
import SearchResult from './components/SearchResult.vue';
import Mapping from './components/Map.vue';

export default {
    setup() {
        const leftDrawerOpen = ref(false);
        const rightDrawerOpen = ref(false);
        return {
            text: ref(""),
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
    components: { SearchResult, Mapping}
}
</script>