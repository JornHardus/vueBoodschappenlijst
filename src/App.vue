<script setup>
import {reactive, ref, computed} from 'vue'

const groceries = reactive([
  {name:'kaas', price:'5', quantity:'1'},
  {name:'wol', price:'1', quantity:'1'},
  {name:'Augurk', price:'3', quantity:'1'},

]);

function submit() {
  this.$refs.form.$el.submit()
}


const calculateTotal = computed(() => {
  return groceries.reduce((totalPrice, item) => totalPrice += item.price * item.quantity, 0);
});

</script>

<template>
  <p>boodschappen</p>
  <form ref="form">
  <li v-for ="groc in groceries">{{ groc }} <input type="number" v-model="groc.quantity"></li>
  <td>{{calculateTotal}} Euro</td>
</form>
</template>