<template>
  <div class="card">
    <img alt="" class="card-img-top" src="../assets/images/1.jpg">


    <div class="card-body">
      <h4 class="card-title">{{ productItems.TenSP }} </h4>
      <p class="card-text">{{ productItems.MoTa }}</p>
      <p>Giá: {{ (productItems.GiaSP).toString() }} VNĐ</p>
    </div>
    <div class="card-footer">
      <button class="btn btn-danger" @click="muaSanPham(productItems)">
        Mua
      </button>
      <button class="btn btn-info" @click="xemChiTiet">
        Xem Chi Tiết
      </button>
    </div>
  </div>





  <teleport to="#app">
    <app-modal v-if="isOpenModalDetail" :isCloseModal="dongModal">
      <h1>Noi dung</h1>
    </app-modal>
  </teleport>

</template>

<script>
export default {
  data() {
    return {
      isOpenModalDetail: false
    }
  },
  methods: {
    xemChiTiet() {
      this.isOpenModalDetail = true
    },
    dongModal() {
      this.isOpenModalDetail = false
    },

    muaSanPham(productItems) {
      this.$emit('handleMuaSanPham', productItems)
    }
  },

  props: {
    productItems: {
      type: Object,
      required: true
    }
  },
  name: "ProductItems.vue"
}
</script>

<style scoped>

</style>
