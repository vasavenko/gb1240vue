<template>
  <div>
    <button :class="[$style.btn]" @click="formVisible">
      ADD NEW COST &nbsp;&nbsp;+
    </button>
    <div :class="[$style.addForm]" v-if="addForm">
      <input :class="[$style.inp]" placeholder="Payment date" v-model="date" />
      <input
        :class="[$style.inp]"
        placeholder="Payment description"
        v-model="category"
      />
      <input
        :class="[$style.inp]"
        type="number"
        placeholder="Payment amount"
        v-model="price"
      />
      <button :class="[$style.addbtn]" @click="save">
        ADD &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; +
      </button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      date: '',
      category: '',
      price: '',
      addForm: false,
    }
  },
  methods: {
    save() {
      const {date, category, price} = this
      // price=Number(price)
      this.$emit('add', {date, category, price})
    },
    formVisible() {
      this.addForm = !this.addForm
      this.price = ''
      this.date = ''
      this.category = ''
    },
  },
}
</script>

<style module>
.addForm {
  position: absolute;
  left: 380px;
  display: flex;
  flex-direction: column;
  /* box-shadow: 0 0 5px rgb(0 0 0 / 62%); */
  border-radius: 5px;
  box-sizing: border-box;
  background-color: white;
  /* padding: 20px; */
  color: black;
}
.inp {
  padding: 10px;
  margin-bottom: 5px;
  align-self: end;
}
.btn {
  width: 150px;
  padding: 8px;
  align-self: end;
  background: rgb(93, 180, 164);
  color: #fff;
  text-align: end;
  margin-bottom: 16px;
}
.addbtn {
  width: 150px;
  padding: 8px;
  align-self: end;
  background: rgb(93, 180, 164);
  color: #fff;
  text-align: end;
}
</style>
