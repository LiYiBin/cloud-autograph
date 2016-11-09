<template>
  <div id="app">
    <AutographPaper
      ref="autograph"
      :watermarkingTxt="watermarkingTxt"
    ></AutographPaper>
    <FunctionsBox
      :onSubmit="handleSubmitWatermarking"
      :onClickPrinting="handleClickPrinting"
    ></FunctionsBox>
  </div>
</template>

<script>
import AutographPaper from './components/AutographPaper';
import FunctionsBox from './components/FunctionsBox';

export default {
  components: {
    AutographPaper,
    FunctionsBox,
  },
  data() {
    return {
      watermarkingTxt: '',
    };
  },
  methods: {
    handleSubmitWatermarking(txt) {
      this.watermarkingTxt = txt;
    },
    handleClickPrinting() {
      this.$refs.autograph.$emit('downloadPng');
    },
  },
};
</script>

<style>

body {
  margin: 0;
}

#app {
  position: relative;
}

</style>
