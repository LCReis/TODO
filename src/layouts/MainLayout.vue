<template>
  <q-layout view="hhh LpR lFf">

    <q-header elevated class="bg-primary text-white">
      <q-toolbar>
        <q-btn dense flat round icon="menu" @click="openMenu" />

        <q-toolbar-title>
          <q-avatar>
            <img src="https://cdn.quasar.dev/logo/svg/quasar-logo.svg">
          </q-avatar>
          Title
        </q-toolbar-title>
      </q-toolbar>
    </q-header>

      <q-drawer v-model="left" side="left" behavior="desktop" elevated bordered content-class="bg-grey-3" overlay>
      <q-scroll-area class="fit">
        <div>
          <q-list v-for="(menuItem, index) in menuList" :key="index">
            <q-item clickable :to="{ name: menuItem.name }">
              <q-item-section avatar>
                <q-icon :name="menuItem.icon" />
              </q-item-section>
              <q-item-section>
                {{ menuItem.label }}
              </q-item-section>
            </q-item>
          <q-separator v-if="menuItem.separator" />
        </q-list>
        </div>
      </q-scroll-area>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>

  </q-layout>
</template>

<script>
const menuList = [
  {
    name: 'Todo',
    icon: 'list',
    label: 'TODO',
    separator: true
  }
]

export default {
  name: 'MainLayout',
  data () {
    return {
      menuList,
      left: false,
      leftDrawerOpen: false
    }
  },

  methods: {
    openMenu () {
      // eslint-disable-next-line no-return-assign
      return this.left = !this.left
    }
  }
}
</script>
