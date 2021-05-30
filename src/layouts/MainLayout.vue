<template>
  <q-layout view="lHh Lpr lFf">
    <q-header class="transparent">
      <div class="glow">
        <q-toolbar class="transparent">
          <q-btn
            flat
            icon="link"
            class="q-mr-sm"
            aria-label="Menu"
            @click="leftDrawerOpen = !leftDrawerOpen"
          />
          <q-space />
          <q-btn-dropdown color="primary" flat dropdown-icon="change_history">
            <q-list>
              <q-item clickable v-close-popup>
                <q-btn flat icon="link">hola</q-btn>
              </q-item>

              <q-item clickable v-close-popup>
                <q-item-section>
                  <q-item-label class="glow">Videos</q-item-label>
                </q-item-section>
              </q-item>

              <q-item clickable v-close-popup>
                <q-item-section>
                  <q-item-label>Articles</q-item-label>
                </q-item-section>
              </q-item>
            </q-list>
          </q-btn-dropdown>
        </q-toolbar>
      </div>

      <!-- <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="leftDrawerOpen = !leftDrawerOpen"
        />

        <q-toolbar-title>
          Quasar App
        </q-toolbar-title>

        <div>Quasar v{{ $q.version }}</div>
      </q-toolbar> -->
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      behavior="mobile"
      overlay
      bordered
    >
      <q-list>
        <q-item-label header class="text-white text-h4 text-bold">
          Relevant Links
        </q-item-label>
        <EssentialLink
          v-for="link in essentialLinks"
          :key="link.title"
          v-bind="link"
        />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import EssentialLink from "components/EssentialLink.vue";

const linksData = [
  {
    title: "Docs",
    caption: "quasar.dev",
    icon: "school",
    link: "https://quasar.dev"
  },
  {
    title: "Github",
    caption: "github.com/quasarframework",
    icon: "code",
    link: "https://github.com/quasarframework"
  },
  {
    title: "Discord Chat Channel",
    caption: "chat.quasar.dev",
    icon: "chat",
    link: "https://chat.quasar.dev"
  },
  {
    title: "Forum",
    caption: "forum.quasar.dev",
    icon: "record_voice_over",
    link: "https://forum.quasar.dev"
  },
  {
    title: "Twitter",
    caption: "@quasarframework",
    icon: "rss_feed",
    link: "https://twitter.quasar.dev"
  },
  {
    title: "Facebook",
    caption: "@QuasarFramework",
    icon: "public",
    link: "https://facebook.quasar.dev"
  },
  {
    title: "Quasar Awesome",
    caption: "Community Quasar projects",
    icon: "favorite",
    link: "https://awesome.quasar.dev"
  }
];

export default {
  name: "MainLayout",
  components: { EssentialLink },
  data() {
    return {
      leftDrawerOpen: false,
      essentialLinks: linksData
    };
  }
};
</script>
<style lang="scss" scoped>
.drawer-bg {
  background: rgb(2, 0, 36);
  background: linear-gradient(
    0deg,
    rgba(2, 0, 36, 0) 0%,
    rgba(0, 212, 255, 1) 100%
  );
}
</style>
