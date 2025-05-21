<template>
  <v-app>
    <v-toolbar color="indigo" dark>
      <v-toolbar-title>Hello Vuetify 1.5</v-toolbar-title>
    </v-toolbar>
    <img class="backdrop" ref="backdrop" src="./assets/sunset.jpeg">
    <img class="mask" src="./assets/mask.png">
    <v-container>
      <div class="main">
        <Introduction :backdropHeight="backdropHeight"></Introduction>
        <!--<v-btn color="primary">Click me</v-btn>-->
      </div>
      <Page :backdropHeight="backdropHeight"></Page>
    </v-container>
    <ScrollBar></ScrollBar>
  </v-app>
</template>

<script>
import { onMounted, ref } from 'vue';
import Introduction from './components/Introduction.vue';
import ScrollBar from './components/ScrollBar.vue';
import Page from './components/Page.vue';

export default {
  name: 'App',
  components: {
    Introduction,
    ScrollBar,
    Page
  },
  data() {
    return {
      stage: 1
    };
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
  },
  mounted() {
    window.addEventListener('scroll', this.handleScroll);
  },
  beforeUnmount() {
    window.removeEventListener('scroll', this.handleScroll);
  },
  methods: {
    handleScroll() {

      if (window.scrollY + window.innerHeight + 10 < this.backdropHeight * this.stage) return;

      scroll(0, this.backdropHeight * this.stage, "smooth");

      this.stage++;

    }
  }
}
</script>

<style>

html {
  scroll-behavior: smooth;
}

.backdrop {
  position: absolute;
  z-index: 0;
  width: 100%;
}

.bd2 {
  position: absolute;
  z-index: 0;
  width: 100%;
}

.mask {
  position: absolute;
  z-index: 2;
  width: 100%;
}

.main {
  position: relative;
  z-index: 1;
}

body::-webkit-scrollbar {
  display: none;
}

</style>