<template>
  <div class="box-autograph-paper">
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
    const width = Math.max(window.innerWidth, window.innerHeight) - 64;

    return {
      canvas: null,
      width,
      height: width * (1 / 4),
    };
  },
  mounted() {
    this.canvas = new fabric.Canvas('js-autograph-paper', {
      width: this.width,
      height: this.height,
      isDrawingMode: true,
    });
    this.canvas.freeDrawingBrush.width = 5;

    this.$on('downloadAutographPng', () => {
      const download = document.createElement('a');
      download.href = this.canvas.toDataURL('png');
      download.download = 'cloud-autograph.png';
      download.click();
    });

    this.$on('submitWatermarking', (txt) => {
      if (txt.length !== 0) {
        const text = new fabric.Text(txt, {
          angle: -22.5,
          textAlign: 'center',
          fill: '#6A6A6A',
          opacity: 0.5,
        });
        this.canvas.add(text);
        text.center();
      }

      this.canvas.isDrawingMode = false;
    });
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

.box-autograph-paper {
  background-color: white;
  display: inline-block;
}

</style>
