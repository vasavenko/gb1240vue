<template>
  <div>
    <table :class="[$style.table]">
      <tbody>
        <tr :class="[$style.tr]">
          <td><b>#&nbsp;</b></td>
          <td><b>Date</b></td>
          <td><b>Category</b></td>
          <td><b>Value</b></td>
        </tr>
        <tr :class="[$style.tr]"
          v-for="(item, index) in curentPage" 
          :key="index"
        >
          <td>{{ index + (page-1)*perPage + 1}}</td>
          <td>{{ item.date }}</td>
          <td>{{ item.category }}</td>
          <td>{{ item.price }}</td>
        </tr>
      </tbody>
    </table>
    <Pagination :length='getPaymentsList.length' 
      :perPage='perPage' 
      :curPage='page'
      @paginate='onPaginate'
    />
  </div>
</template>

<script>

import { mapGetters } from 'vuex'
import Pagination from './Pagination'

export default {
  components: {
    Pagination
  },
  data () {
    return {
    page: 1,
    perPage: 3
    }
  },
  computed: {
    ...mapGetters(['getPaymentsList']),
    curentPage () {
      const { page, perPage } = this
      return this.getPaymentsList.slice(perPage*(page-1), perPage*(page-1)+perPage )
    }
  },
  methods: {
    onPaginate (p){
      this.page = p
    }
  }
}
</script>

<style module>
.table {
  width: 350px;
  border-collapse: collapse;
}
.tr {
  height: 36px;
  border-bottom: 1px solid rgba(138, 138, 138, 0.5);
}
</style>
