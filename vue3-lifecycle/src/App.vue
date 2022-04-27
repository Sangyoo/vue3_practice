<template>
  <h1>{{ count }}</h1>
</template>

<script>
/*
https://kr.vuejs.org/images/lifecycle.png
1. create - 컴포넌트를 코드가 쓰여진 대로 생성하는 단계
2. mount - 컴포넌트를 html 구조에 연결시키는 단계*/ 
export default{
  data() {
    return {
      count: 2
    }
  },
  //beforecreate라는 lifecycle hook은 컴포넌트가 생성되기 직전에 실행된다. 
  //데이터가 정의되지 않았다. count -undefined
  beforeCreate() {
    console.log('before create!', this.count)
  },
  //created는 component가 생성된 직후에 실행됨
  created() {
    console.log('created!', this.count)
  },
  //h1태그를 출력할 수 없다. mount라는 것이 컴포넌트를 html구조에 연결하는 것이기 때문에
  //beforeMount는 html 태그를 조회할 수 없다.
  beforeMount(){
    console.log('before mounted!')
    console.log(document.querySelector('h1'))
  },
  //component가 출력되고 난 후에 실행됨.여기서는 count 출력 후에
  mounted() {
    console.log('mounted!')
    console.log(document.querySelector('h1'))
  },
}
</script>

