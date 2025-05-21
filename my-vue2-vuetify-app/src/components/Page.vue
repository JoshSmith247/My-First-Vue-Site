<template>
  <div id="container" :style="{ marginTop: backdropHeight + 'px' }">
    <div v-for="(item, index) in items" :key="index" class="block">
      <div id="container-2" :style="{ marginTop: backdropHeight + 'px' }">
        <img class="bd2" :src="getSrc(index + 1)" alt="photo">
        <h1>Reason {{ index + 1 }}</h1>
        <p>{{ item.text }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Page',
  props: {
    backdropHeight: {
      type: Number,
      required: true
    }
  },
  data() {
    return {
      items: [
        { text: 'Heyyyyyy' },
        { text: 'She always listens' },
        { text: 'She makes the best tea' }
        // Add more items as you like
      ]
    };
  },
  methods: {
    getSrc(idx) {
      try {
        return require('../assets/pages/mylove' + idx + '.jpeg');
      } catch (err) {
        console.warn("Image " + idx + " not found");
        return '';
      }
    }
  }
}
</script>

<style scoped>

#container {
  margin-top: 200px;
}

p, h1 {
  position: relative;
}

.bd2 {
  width: 120%;
  margin: -15%;
}

</style>
