<template>
  <div class="scroll-container">
    <h1>[ Scroll to see ]</h1>
  </div>
</template>

<style scoped>

.scroll-container {
    position: fixed;
    bottom: 0px;
    width: 100%;
    height: 100px;
    background-image: linear-gradient(rgba(0,0,0,0), rgba(0,0,0,1));
    z-index: 1;
}

h1 {
    color: white;
    text-align: center;
}

</style>