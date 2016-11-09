<template>
  <div>
    <canvas id="js-autograph-paper"></canvas>
  </div>
</template>

<script>
import Fabric from 'fabric';

export default {
  mounted() {
    /* eslint-disable new-cap */
    const canvas = new Fabric.fabric.Canvas('js-autograph-paper', {
      width: window.innerWidth,
      height: window.innerHeight,
      isDrawingMode: true,
    });
    canvas.freeDrawingBrush.width = 10;
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

#js-autograph-paper {
  width: 100vw;
  height: 100vh;
}

</style>
