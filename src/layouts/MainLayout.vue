<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="toggleLeftDrawer"
        />

        <q-toolbar-title> Quasar App </q-toolbar-title>

        <div>Quasar v{{ $q.version }}</div>
      </q-toolbar>
    </q-header>

    <q-drawer v-model="leftDrawerOpen" show-if-above bordered>
      <q-list>
        <q-item-label header> Essential Links </q-item-label>
        <component-link
          v-for="link in componentLinks"
          :key="link.title"
          v-bind="link"
        >
        </component-link>
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import ComponentLink, {
  ComponentLinkProps,
} from 'components/ComponentLink.vue';

const componentLinks: ComponentLinkProps[] = [
  {
    title: 'Ana Sayfa',
    caption: 'quasar.dev',
    icon: 'school',
    link: '/',
  },
  {
    title: 'SAYFA 1',
    caption: 'github.com/quasarframework',
    icon: 'code',
    link: '/page1',
  },
  {
    title: 'SAYFA 2',
    caption: 'chat.quasar.dev',
    icon: 'chat',
    link: '/page2',
  },
  {
    title: 'SAYFA 3',
    caption: 'forum.quasar.dev',
    icon: 'record_voice_over',
    link: 'page3',
  },
  {
    title: 'SAYFA 4',
    caption: '@quasarframework',
    icon: 'rss_feed',
    link: '/page4',
  },
  {
    title: 'SAYFA 5',
    caption: '@QuasarFramework',
    icon: 'public',
    link: '/page5',
  }
];

const leftDrawerOpen = ref(false);

function toggleLeftDrawer() {
  leftDrawerOpen.value = !leftDrawerOpen.value;
}
</script>
