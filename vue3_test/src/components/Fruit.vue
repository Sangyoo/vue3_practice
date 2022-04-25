<template>
  <li>{{ name }}</li>
  <!-- <li>{{ bary }}</li> -->
</template>

<script>
export default {
  props: {
    name: {
      type: String,
      default: ''
    },
    // bary: {
    //   type: String,
    //   default: ""
    // }
  }
}
</script>


<style scoped lang="scss">
//scoped는 해당 vue 파일에만 style을 적용한다.
//그래서 선택자를 복잡하게 지정하지 않아도 된다는
//장점이 있다.
  h1{
    color: red !important
  }
</style>