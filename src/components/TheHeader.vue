<template>
  <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
    <a class="navbar-brand" href="#">Navbar</a>
    <button aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation"
            class="navbar-toggler" data-target="#navbarSupportedContent" data-toggle="collapse" type="button">
      <span class="navbar-toggler-icon"></span>
    </button>

    <div id="navbarSupportedContent" class="collapse navbar-collapse">
      <ul class="navbar-nav mr-auto">
        <li class="nav-item active">
          <a class="nav-link" href="#">Home <span class="sr-only">(current)</span></a>
        </li>
        <li class="nav-item">
          <a class="nav-link" href="#">Link</a>
        </li>
        <li class="nav-item dropdown">
          <a id="navbarDropdown" aria-expanded="false" aria-haspopup="true" class="nav-link dropdown-toggle"
             data-toggle="dropdown" href="#" role="button">
            Dropdown
          </a>
          <div aria-labelledby="navbarDropdown" class="dropdown-menu">
            <a class="dropdown-item" href="#">Action</a>
            <a class="dropdown-item" href="#">Another action</a>
            <div class="dropdown-divider"></div>
            <a class="dropdown-item" href="#">Something else here</a>
          </div>
        </li>
        <li class="nav-item">
          <a class="nav-link disabled" href="#">Disabled</a>
        </li>
      </ul>
      <div class="form-inline my-2 my-lg-0">
        <input aria-label="Search" class="form-control mr-sm-2" placeholder="Search" type="search">
        <button class="btn btn-outline-success my-2 my-sm-0" type="submit">Search</button>
        <button class="btn btn-danger ml-4" @click="isOpenModal">
          <i class="fa-solid fa-cart-shopping"></i>
          <span class="ml-3">{{SumAmountCart}}</span>
        </button>
      </div>
    </div>
  </nav>

  <teleport to="body">
    <app-modal v-if="openModal" :isCloseModal="isCloseModal">
      <section>
        <CartList :arraySP="arraySP" @handle-delete-cart="HandleDeleted" @handle-tang-giam-so-luong="HandleTangGiam"/>
      </section>
    </app-modal>
  </teleport>


</template>

<script>
import CartList from "@/components/CartList";

export default {

  computed:{
    SumAmountCart(){
      return this.arraySP.reduce((sp,cart) => (sp += cart.amount),0)
    }
  },

  props: {
    arraySP:{
      type:Array
    }
  },
  components: {
    CartList
  },
  data() {
    return {
      openModal: false
    }
  },
  methods: {
    HandleTangGiam(params){
      console.log('TheHeader',params)
      this.$emit('handle-tang-giam-so-luong',params)
    },
    HandleDeleted(cart){
      this.$emit('handle-delete-cart',cart)
    },
    isOpenModal() {
      this.openModal = true
    },
    isCloseModal() {
      this.openModal = false
    }
  },
  name: "TheHeader.vue"
}
</script>

<style scoped>
</style>
