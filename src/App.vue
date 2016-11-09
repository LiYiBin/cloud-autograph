<template>
  <div id="app">
    <AutographPaper
      :watermarkingTxt="watermarkingTxt"
    ></AutographPaper>
    <FunctionsBox
      :onSubmit="handleSubmitWatermarking"
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
