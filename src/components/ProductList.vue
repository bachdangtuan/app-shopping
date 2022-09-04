<template>
  <section class="container">
    <h1>Sản phẩm nổi bật</h1>

    <div class="product-list row">
      <div class="col-3" v-for="(item,index) in ProductListItems" :key="index">
        <ProductItems :productItems="item" @handleMuaSanPham="handleMuaSanPham"></ProductItems>
      </div>
    </div>


  </section>

</template>

<script>
import ProductItems from "@/components/ProductItems";


export default {
  methods:{
    handleMuaSanPham(productItems){
      console.log('produclist',productItems)
      this.$emit('handleMuaSanPham',productItems)
    }
  },
  data(){
    return {
      ProductListItems:[
        {
          "TenSP": "Bàn phím loại 1",
          "GiaSP": "100000",
          "HinhSP": "1.jpg",
          "MoTa": "Bàn phím đẹp, giá rẻ bất ngờ",
          "MaSP": 1
        },
        {
          "TenSP": "Bàn phím loại 2",
          "GiaSP": "130000",
          "HinhSP": "2.jpg",
          "MoTa": "Bàn phím đẹp, giá rẻ bất ngờ",
          "MaSP": 2
        },
        {
          "TenSP": "Bàn phím loại 3",
          "GiaSP": "150000",
          "HinhSP": "../assets/images/3.jpg",
          "MoTa": "Bàn phím đẹp, giá rẻ bất ngờ",
          "MaSP": 3
        },
        {
          "TenSP": "Bàn phím loại 4",
          "GiaSP": "160000",
          "HinhSP": "../assets/images/4.jpg",
          "MoTa": "Bàn phím đẹp, giá rẻ bất ngờ",
          "MaSP": 4
        },
        {
          "TenSP": "Bàn phím loại 5",
          "GiaSP": "250000",
          "HinhSP": "../assets/images/5.jpg",
          "MoTa": "Bàn phím đẹp, giá rẻ bất ngờ",
          "MaSP": 5
        },
        {
          "TenSP": "Bàn phím loại 7",
          "GiaSP": "230000",
          "HinhSP": "../assets/images/7.jpg",
          "MoTa": "Bàn phím đẹp, giá rẻ bất ngờ",
          "MaSP": 6
        },
        {
          "TenSP": "Bàn phím loại 1",
          "GiaSP": "230000",
          "HinhSP": "../assets/images/1.jpg",
          "MoTa": "Bàn phím đẹp, giá rẻ bất ngờ",
          "MaSP": 7
        },
        {
          "TenSP": "Bàn phím loại 1",
          "GiaSP": "230000",
          "HinhSP": "../assets/images/1.jpg",
          "MoTa": "Bàn phím đẹp, giá rẻ bất ngờ",
          "MaSP": 8
        },
      ]
    }
  },


  components: {
    ProductItems
  },
  name: "ProductList.vue"
}
</script>

<style scoped>
</style>
