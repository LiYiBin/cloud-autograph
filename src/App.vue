<template>
  <div id="app">
    <AutographPaper></AutographPaper>
    <FunctionsBox
      :onSubmit="handleSubmitWatermarking"
    ></FunctionsBox>
  </div>
</template>

<script>
import AutographPaper from './components/AutographPaper';
import FunctionsBox from './components/FunctionsBox';

export default {
  name: 'app',
  components: {
    AutographPaper,
    FunctionsBox,
  },
  methods: {
    handleSubmitWatermarking(txt) {
      console.log(txt);
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
