<template>
  <div :class="positionClass">
    <div :style="{ marginTop: -backdropHeight * 0.1 + 'px' }" :class="titleVisibleClass">
      <h1>101 reasons</h1>
      <h1>I love</h1>
      <h1>Alexa Hatcher</h1>
    </div>
    <p id="comprehension" :class="compVisibleClass" :style="{ top: backdropHeight * 0.515 + 'px' }">(The comprehensive list)</p>
  </div>
</template>

<script>
export default {
  name: 'Introduction',
  data() {
    return {
      isFixed: true,
      compVisible: true,
      titleVisible: true
    };
  },
  props: {
    backdropHeight: {
      type: Number,
      required: true
    }
  },
  computed: {
    positionClass() {
      return !this.isFixed ? 'fixed-position' : 'absolute-position';
    },
    compVisibleClass() {
      return this.compVisible ? 'visible-comp' : 'invisible';
    },
    titleVisibleClass() {
      return this.titleVisible ? 'visible-title' : 'invisible';
    }
  },
  mounted() {
    window.addEventListener('scroll', this.handleScroll);
  },
  beforeUnmount() {
    window.removeEventListener('scroll', this.handleScroll);
  },
  methods: {
    handleScroll() {
      this.isFixed = window.scrollY < 50;
      this.compVisible = window.scrollY < 15;
      this.titleVisible = window.scrollY < this.backdropHeight * 0.6;
    }
  }
}
</script>

<style scoped>

h1 {
  font-size: 60px;
  color: #333333;
}

h3 {
  margin: 40px 0 0;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}

p {
  color: white;
}

.fixed-position {
  position: fixed;
  top: 150px;
  width: 100%;
}

.absolute-position {
  position: absolute;
  top: 110px;
  left: 0;
  width: 100%;
}

.visible-comp {
  position: fixed;
  z-index: 2;
}

.visible-title {
  z-index: 2;
}

.invisible {
  display: none;
}

/*.fixed-position, .absolute-position, .visible, .invisible {
  transition: all 0.3s ease;
}*/

</style>
