<template>
<div>
  <input id="fname" type="text" v-model="fnameinit" @change="fnameValidate"/>
  <label>{{fname}}</label>
  <input id="lname" type="text"/>
  <label>{{datafromendpoint}}</label>
  <input id="email" type="text"/>
  <input id="message" type="text"/>
  <input id="phonenumber" type="text"/>
  <button @click="somevent">submit</button>
</div>
</template>

<script setup lang="ts">


import { ref, defineEmits } from 'vue'
import  axios  from 'axios'
let datafromendpoint
axios.get('https://95o5gv-8124.sse.codesandbox.io/endpoint-1').then((response) => {
console.log(response)
datafromendpoint = response.data
}).catch((error) => {
  console.log(error)
})

const emit = defineEmits(['form-submitted'])
  const fname = ref('')
   const fnameinit = ref('')



  function fnameValidate() {
    if (fnameinit.value.includes('#')) {
      console.log('error')
      fname.value = 'error'
    } else {
      fname.value = ''
    }
  }

  function somevent(e : PointerEvent) { 
    emit('form-submitted')
    
  }



</script>