<template>
  <div class="alert alert-danger" v-if="isValidForm" role="alert">
    <p v-if='nameIsError'><strong>Name:</strong> value is incorrect</p>
    <p v-if='emailIsError'><strong>E-mail:</strong> value is incorrect</p>
    <p v-if='ageIsError'><strong>Age:</strong> value is incorrect</p>
  </div>
</template>

<script>
export default {
  name: "Error",
  props: ['nameIsError', 'emailIsError', 'ageIsError', 'isValidForm']
}
</script>

<style scoped>

</style>