<template>
  <v-app>
    <v-container :fluid="true">
      <v-navigation-drawer v-model="drawer">

        <v-img
          class="me-sm-8"
          max-width="40"
          src="https://cdn.vuetifyjs.com/docs/images/logos/v.svg"
        />

        <v-list density="compact">
          <v-list-item
            v-for="(item,i) in menuList"
            :key="i"
            :value="item"
            color="primary"
            @click="movePage(item)"
          >
            <template v-slot:prepend>
              <v-icon :icon="item.prependIcon"></v-icon>
            </template>
            <v-list-item-title v-text="item.title"></v-list-item-title>
          </v-list-item>
        </v-list>
      </v-navigation-drawer>

      <!--<v-app-bar class="px-md-4">
        <v-app-bar-title>Application Bar</v-app-bar-title>
      </v-app-bar>-->

      <v-main>
        <router-view />
      </v-main>
    </v-container>
  </v-app>
</template>

<script setup>
  import { useRouter } from 'vue-router';
  import { ref } from 'vue'

  import { onMounted } from 'vue'

  const router = useRouter();

  const drawer = ref(true)

  const menuList = ref([
    {
      title: 'Character',
      pathName: 'character',
      prependIcon: 'mdi-view-dashboard-outline',
      link: true,
    },
    {
      title: 'School',
      pathName: 'school',
      prependIcon: 'mdi-account-group',
      link: true,
    }
  ])

  function movePage(item){
    router.push({name : item.pathName});
  }
</script>

<style>
/*scroll inactive*/
html { 
  overflow-y: auto !important 
}
</style>