<template>
  <nav aria-label="Page navigation example">
  <ul class="pagination mt-3">
    <li class="page-item" :class="{'disabled':page.current_page===1 }"
    @click.prevent=change(page.current_page-1)>
      <a class="page-link" href="#" aria-label="Previous">
        <span aria-hidden="true">&laquo;</span>
      </a>
    </li>
    <li class="page-item" v-for="(item,index) in page.total_pages" :key="index" :class="{'active':page.current_page===item}">
        <a class="page-link" href="#" @click.prevent="change(item)">{{item}}</a>
    </li>
    <li class="page-item" :class="{'disabled':page.current_page===page.total_pages }"
    @click.prevent=change(page.current_page+1)>
      <a class="page-link" href="#" aria-label="Next">
        <span aria-hidden="true">&raquo;</span>
      </a>
    </li>
  </ul>
</nav>
</template>

<script>
export default {
  props: ['page'],
  methods: {
    change (item) {
      this.$emit('change-page', item)
    }
  }
}
</script>
