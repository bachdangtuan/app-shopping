<template>
  <div class="modal" @click="isCloseModal">
    <div class="modal__container" @click.stop>
      <div class="modal__header">
        <h1 class="modal__title">Cart</h1>
        <div class="modal__close" @click="isCloseModal">
          <i class="fa fa-times"></i>
        </div>
      </div>
      <div class="modal__content">
        <slot></slot>
      </div>
      <div class="modal__footer">
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    isCloseModal: {
      type: Function,
    },
  },


  name: "AppModal.vue"
}
</script>

<style scoped>

.modal {
  position: fixed;
  z-index: 1000;
  left: 0;
  right: 0;
  display: flex;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.4);
}

.modal__container {
  width: 950px;
  margin: auto;
  margin-top: 70px;
  background: white;
  border: 10px;
}

.modal__header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.modal__close {
  width: 50px;
  height: 50px;
  line-height: 50px;
  border-radius: 50%;
  text-align: center;
  font-size: 30px;
}

.modal__close:hover {
  background-color: rgba(0, 0, 0, 0.2);
  cursor: pointer;
}
</style>
