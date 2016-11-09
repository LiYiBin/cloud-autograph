<template>
  <footer id="footer">
    <button class="btn-add" type="button" name="button"
      @click="handleClickAdd"
    >
      <img src="../assets/ic_add_white_48px.svg" alt="add" />
    </button>


    <div class="modal-watermarking"
      v-show="isShowModal"
    >
      <h2 class="modal-watermarking__txt">浮水印</h2>
      <input v-model="watermarkingTxt" class="modal-watermarking__input" type="text" name="watermarking">
      <button class="modal-watermarking__btn" type="button" name="button"
        @click="handleSubmit"
      >
        新增
      </button>
    </div>
  </footer>
</template>

<script>

export default {
  props: [
    'onSubmit',
  ],
  data() {
    return {
      isShowModal: false,
      watermarkingTxt: '',
    };
  },
  methods: {
    handleClickAdd() {
      this.isShowModal = !this.isShowModal;
    },
    handleSubmit() {
      this.isShowModal = false;
      this.onSubmit(this.watermarkingTxt);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

#footer {
  position: fixed;
  left: 0; bottom: 0; right: 0;
  height: 100px;
  background-color: black;
  z-index: 999;
  display: flex;
  justify-content: center;
  align-items: center;
}

.btn-add {
  border: 0; outline: 0;
  background-color: transparent;
  cursor: pointer;
}

.modal-watermarking {
  box-sizing: border-box;
  position: absolute;
  bottom: 100px;
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
  width: 80%; height: 40%;
  margin: 32px auto;
  font-size: 24px;
}

.modal-watermarking__btn {
  padding: 8px 16px;
}

</style>
