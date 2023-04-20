<template>
<FormComponent v-on:form-submitted="heard"/>
</template>

<script setup lang="ts">
import FormComponent from '../components/FormComponent.vue'
function heard(){
  console.log('submitted')
}
</script>