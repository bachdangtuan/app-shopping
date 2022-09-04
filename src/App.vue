<template>
  <header>
    <the-header :arraySP="arraySP" @handle-delete-cart="HandleDeleted" @handle-tang-giam-so-luong="HandleTangGiam"/>
  </header>
  <section>
    <ProductList @handleMuaSanPham="handleMuaSanPham"/>
  </section>

</template>

<script>

import TheHeader from "@/components/TheHeader";
import ProductList from "@/components/ProductList";


export default {

  methods: {
    //Tăng Giảm Số Lượng
    HandleTangGiam(params) {
      // console.log('app',params)
      const {status, cart} = params;
      let index = this.arraySP.findIndex(sp => {
        return sp.MaSP === cart.MaSP
      })
      if (index !== -1) {
        if (status === true) {
          if (this.arraySP[index].totalAmount - this.arraySP[index].amount > 0) {
            this.arraySP[index].amount += 1
          } else {
            this.arraySP[index].amount += 0
          }
        }
        if (status === false) {
          if (this.arraySP[index].amount === 0) {
            this.arraySP[index].amount -= 0
          } else {
            this.arraySP[index].amount -=1
          }
          // this.arraySP[index].amount -= 1
        }
      }
    },

    //Mua sản phẩm
    handleMuaSanPham(productItems) {
      let index = this.arraySP.findIndex(cart => {
        return cart.MaSP === productItems.MaSP
      })
      console.log('index', index)
      if (index !== -1) {
        this.arraySP[index].amount += 1
      } else {
        const newProductItems = {...productItems, amount: 1, totalAmount: 1000}
        this.arraySP = [...this.arraySP, newProductItems]
      }
      // this.arraySP.push(productItems)

    },
    //Xóa Sản Phẩm
    HandleDeleted(cart) {
      console.log('App', cart)
      this.arraySP = this.arraySP.filter(cartItem => cartItem.MaSP !== cart.MaSP)
    }


  },

  data() {
    return {
      arraySP: []
    }
  },
  name: 'App',
  components: {
    TheHeader,
    ProductList,

  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
