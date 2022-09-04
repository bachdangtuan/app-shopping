<template>
  <table class="table text-center">
    <thead>
    <tr>
      <th>STT</th>
      <th>Tên</th>
      <th>Đơn Giá</th>
      <th>Số lượng Trong Kho</th>
      <th>Số lượng</th>
      <th>Thành Tiền</th>
      <th>Hành Động</th>
    </tr>
    </thead>
    <tbody>
    <tr v-for="(cart,index) in arraySP" :key="index">
      <td scope="row">1</td>
      <td>{{ cart.TenSP }}</td>
      <td>{{ cart.GiaSP }}</td>
      <td>{{ cart.totalAmount - cart.amount }}</td>
      <td>
        <button class="btn btn-primary" @click="TangSoLuon(true,cart)">
          <i class="fa fa-arrow-up"></i>
        </button>
        {{ cart.amount }}
        <button class="btn btn-danger mx-2" @click="TangSoLuon(false,cart)">
          <i class="fa fa-arrow-down"></i>
        </button>
      </td>
      <td>{{ cart.amount * cart.GiaSP }}</td>
      <td>
        <button class="btn btn-danger" @click="handleDeleted(cart)">
          <i class="fa fa-trash-alt"></i>
        </button>
      </td>
    </tr>
    </tbody>

    <tfoot>
    <tr>
      <td>Tổng tiền là</td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td>{{ sumMoney }}</td>
    </tr>
    </tfoot>


  </table>
</template>

<script>
export default {

  computed: {
    sumMoney() {
     return this.arraySP.reduce((sum, cart) => sum += cart.amount * cart.GiaSP, 0)
    }
  },

  methods: {

    TangSoLuon(status, cart) {
      this.$emit('handle-tang-giam-so-luong', {status, cart})
    },

    handleDeleted(cart) {
      console.log('cart', cart)
      this.$emit("handle-delete-cart", cart)
    }
  },
  props: {
    arraySP: {
      type: Array
    },
  },

  name: "CartList.vue"
}
</script>

<style scoped>

</style>
