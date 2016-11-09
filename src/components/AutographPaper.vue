<template>
  <div>
    <canvas id="js-autograph-paper"></canvas>
  </div>
</template>

<script>
import { fabric } from 'fabric';

export default {
  props: [
    'watermarkingTxt',
  ],
  data() {
    return {
      canvas: null,
      width: window.innerWidth,
      height: window.innerHeight,
    };
  },
  watch: {
    watermarkingTxt(newValue) {
      if (newValue.length !== 0) {
        const text = new fabric.Text(newValue, {
          left: this.width * 0.2,
          top: this.height * 0.2,
          fill: '#6A6A6A',
          opacity: 0.5,
        });
        this.canvas.add(text);
      }

      this.canvas.isDrawingMode = false;
    },
  },
  mounted() {
    this.canvas = new fabric.Canvas('js-autograph-paper', {
      width: this.width,
      height: this.height,
      isDrawingMode: true,
    });
    this.canvas.freeDrawingBrush.width = 10;

    this.$on('downloadPng', () => {
      const download = document.createElement('a');
      download.href = this.canvas.toDataURL('png');
      download.download = 'cloud-autograph.png';
      download.click();
    });
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
