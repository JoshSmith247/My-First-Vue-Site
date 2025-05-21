<template>
  <div id="container" :style="{ marginTop: backdropHeight + 'px' }">
    <div v-for="(item, index) in items" :key="index" class="block">
      <div id="container-2" :style="{ marginTop: backdropHeight + 'px' }">
        <img class="bd2" :src="item.img" alt="photo">
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
        { img: require('../assets/mylove.jpeg'), text: 'Heyyyyyy' },
        { img: require('../assets/mylove.jpeg'), text: 'She always listens' },
        { img: require('../assets/mylove.jpeg'), text: 'She makes the best tea' }
        // Add more items as you like
      ]
    };
  }
}
</script>

<style scoped>

#container {
  margin-top: 200px;
}

p {
  position: relative;
}

.bd2 {
  width: 120%;
  margin: -15%;
}

</style>
