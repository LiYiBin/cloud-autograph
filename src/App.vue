<template>
  <div id="app">
    <div class="overlay">
      <img src="./assets/ic_3d_rotation_black_48px.svg" alt="hint-rotation" />
    </div>

    <header id="header">
      <h2 class="header-title">簽名</h2>
    </header>

    <AutographPaper ref="autograph" />

    <div class="modal-watermarking"
      v-show="isShowModal"
    >
      <h2 class="modal-watermarking__txt">浮水印</h2>
      <textarea v-model="watermarkingTxt" class="modal-watermarking__input" name="watermarking"></textarea>
      <button class="modal-watermarking__btn" type="button" name="button"
        @click="handleSubmitWatermarking"
      >
        新增
      </button>
    </div>

    <footer id="footer">
      <button class="btn-icon" type="button" name="button"
        @click="handleClickAdd"
      >
        <img src="./assets/ic_add_white_48px.svg" alt="add" />
      </button>

      <button class="btn-icon" type="button" name="button"
        @click="handleClickPrinting"
      >
        <img src="./assets/ic_local_printshop_white_48px.svg" alt="printing" />
      </button>
    </footer>
  </div>
</template>

<script>
import AutographPaper from './components/AutographPaper';

export default {
  components: {
    AutographPaper,
  },
  data() {
    return {
      isShowRotation: false,
      watermarkingTxt: '',
      isShowModal: false,
    };
  },
  methods: {
    handleClickAdd() {
      this.isShowModal = !this.isShowModal;
    },
    handleSubmitWatermarking() {
      this.isShowModal = false;
      this.$refs.autograph.$emit('submitWatermarking', this.watermarkingTxt);
    },
    handleClickPrinting() {
      this.$refs.autograph.$emit('downloadAutographPng');
    },
  },
};

</script>

<style>

body {
  margin: 0;
  width: 100vw;
  background-color: #EDECED;
}

#app {
  position: relative;
  width: 100%; height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}

.overlay {
  position: fixed;
  top: 0; right: 0; bottom: 0; left: 0;
  z-index: 9999;
  background-color: rgba(0, 0, 0, 0.8);
}

@media (orientation: landscape) {
  .overlay {
    display: none;
  }
}

.overlay img {
  position: absolute;
  top: 50%; left: 50%;
  transform: translate(-50%, -50%);
  width: 25%;
}

#header {
  position: fixed;
  top: 0; right: 0; left: 0;
  height: 50px;
  background-color: #3748AC;
  display: flex;
  justify-content: center;
  align-items: center;
}

.header-title {
  margin: 0;
  color: white;
}

#footer {
  position: fixed;
  left: 0; bottom: 0; right: 0;
  height: 50px;
  padding: 4px;
  background-color: black;
  display: flex;
  justify-content: center;
  align-items: center;
}

.btn-icon {
  border: 0; outline: 0;
  background-color: transparent;
  cursor: pointer;
  margin: 0 16px;
  padding: 0;
}

.modal-watermarking {
  box-sizing: border-box;
  position: absolute;
  top: 50%; left: 50%;
  transform: translate(-50%, -50%);
  width: 80%;
  text-align: center;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-flow: column wrap;
  padding: 32px;
  box-shadow: 0 2px 2px 0 rgba(0,0,0,.14),0 3px 1px -2px rgba(0,0,0,.2),0 1px 5px 0 rgba(0,0,0,.12);
  background-color: #F9F9F9;
}

.modal-watermarking__txt {
  margin: 0;
}

.modal-watermarking__input {
  width: 80%;
  margin: 12px auto;
  font-size: 20px;
}

.modal-watermarking__btn {
  padding: 8px 16px;
  border: 0;
  background-color: #1E8BF1;
  color: white;
}

</style>
