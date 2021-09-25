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
        <tr :class="[$style.tr]" v-for="(item, index) in items" :key="index">
          <td>{{ index + 1 }}</td>
          <td>{{ item.date }}</td>
          <td>{{ item.category }}</td>
          <td>{{ item.price }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  props: {
    items: Array,
  },
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
