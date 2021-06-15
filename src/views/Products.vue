<template>
    <div class="container">
        <div class="row">
            <div class="col-4 mt-3" v-for="item in products" :key="item.id">
                <div class="card h-100">
                    <div class='bg-cover' :style="{backgroundImage:'url('+item.imageUrl+')',height: '200px'}"></div>
                    <!-- <img src="..." class="card-img-top" alt="..."> -->
                    <div class="card-body">
                    <h5 class="card-title">{{item.title}}</h5>
                    <p class="card-text">{{item.content}}</p>
                    </div>
                    <div class="card-footer mb-2 bg-white border-0 d-flex justify-content-between">
                        <button type="button" class="btn btn-primary btn-sm" @click.prevent="change">查看更多</button>
                        <button type="button" class="btn btn-primary btn-sm">加入購物車</button>
                    </div>
                </div>
            </div>
            <div class="d-flex justify-content-center">
                <pagination :page="pagination" @change-page="getProducts"></pagination>
            </div>
        </div>
        <router-view></router-view>
    </div>
</template>
<script>
import pagination from '@/components/Pagination.vue'
export default {
  data () {
    return {
      products: [],
      pagination: {}
    }
  },
  methods: {
    change () {
      this.$router.push('/products/product')
    },
    getProducts (page = 1) {
      this.$http.get(`${process.env.VUE_APP_URL}api/${process.env.VUE_APP_PATH}/products?page=${page}`)
        .then(res => {
          const { products, pagination } = res.data
          this.products = products
          this.pagination = pagination
        //   console.log(res)
        //   console.log(this.products)
        //   console.log(this.pagination)
        })
    }
  },
  mounted () {
    this.getProducts()
    // console.log(process.env.VUE_APP_URL)
    // console.log(process.env.VUE_APP_PATH)
  },
  components: {
    pagination
  }
}
</script>

<style lang="scss">
.bg-cover{
    background-position: center center;
    background-size: cover;
}
</style>
