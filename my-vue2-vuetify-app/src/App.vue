<template>
  <v-app>
    <v-toolbar color="indigo" dark>
      <v-toolbar-title>Hello Vuetify 1.5</v-toolbar-title>
    </v-toolbar>
    <img class="backdrop" ref="backdrop" src="./assets/sunset.jpeg">
    <v-container>
      <div class="main">
        <Introduction :backdropHeight="backdropHeight"></Introduction>
        <!--<v-btn color="primary">Click me</v-btn>-->
      </div>
    </v-container>
    <ScrollBar></ScrollBar>
  </v-app>
</template>

<script>
import { onMounted, ref } from 'vue';
import Introduction from './components/Introduction.vue';
import ScrollBar from './components/ScrollBar.vue';

export default {
  name: 'App',
  components: {
    Introduction,
    ScrollBar
  },
  setup() {
    const backdrop = ref(null);
    const backdropHeight = ref(0);

    onMounted(() => {
      const updateHeight = () => {
        if (backdrop.value) {
          backdropHeight.value = backdrop.value.clientHeight;
        }
      };

      if (backdrop.value) {
        if (backdrop.value.complete) {
          updateHeight();
        } else {
          backdrop.value.onload = updateHeight;
        }

        window.addEventListener("resize", updateHeight);
      }
    });

    return { backdrop, backdropHeight };
  }
}
</script>

<style>

.backdrop {
  position: absolute;
  z-index: 0;
  width: 100%;
}

.main {
  position: relative;
  z-index: 1;
}


</style>