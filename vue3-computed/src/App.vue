<template>
  <button @click="add">add</button>
  <!-- 아래 1번과 2번의 결과는 사실 다른게 없다. 호출할 때마다 결과를 연산해야하지만
3번째의 경우에는 캐싱이라는 기능으로 처음만 계산하고, 다음에 호출할 때에는
계산이 된 상태로 메모리에서 가져오기만한다. 데이터 최적화를 통해 효율 증가 -->
  <h1>{{ msg.split('').reverse().join('') }}</h1>
  <h1>{{ reverseMessage() }}</h1>
  <h1>{{ reversedMessage }}</h1>
</template>

<script>
export default {
  data() {
    return{
      //getter, setter (읽고 바꾸기 가능)
      msg: 'Hello computed!'
    }
  },
  //변경된 데이터를 탐지하는 기능을 가진 'watch'
  watch: {
    msg(newValue) {
      console.log('msg:', newValue)
    },
    reversedMessage(newValue) {
      console.log('reversedMessage:', newValue)
    }
  },
  computed: {
    //data를 가공하여 만든 새로운 데이터. 원본을 훼손하지 않는다.
    //computed에 만들어논 자료는 읽기전용이다.

    // reversedMessage() {
    //   return this.msg.split('').reverse().join('')
    // }

    //그러나 get(), 과 set() 함수를 통해 바꿀 수 있다.

    reversedMessage: /*함수()표시 없는 것 주의*/{
      get() {
        return this.msg.split('').reverse().join('')
      },
      //add함수의 reversedMessage += '!?' 부분이 value에 들어온다.
      //(새로운)reversedMessage 값을 인자로 받는 것이다.
      set(value) {
          this.msg = value
          console.log(value)
      }
    }
  },
  methods: {
    //add라는 메소드를 통해 reversedMessage가 재할당이 되면
    //set이라는 부분의 함수가 실행된다.
    add() {
      this.reversedMessage += '!?'
    },
    reverseMessage() {
      return this.msg.split('').reverse().join('')
    }
  }
}
</script>