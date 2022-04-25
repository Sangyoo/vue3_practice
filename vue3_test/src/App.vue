<template>
  <h1 @click="increase">{{ count }}</h1>
  <div v-if="count>4">
    4보다 큽니다!
  </div>
  <ul>
    <Fruit
      v-for="fruit in fruits"
      :key="fruit"
      :name="fruit"
      :bary="fruit">
      {{ fruits }}
    </Fruit>
    <!-- <hello
      v-for="number in numbers"
      :key="number"
      :name="fruit"
      :bary="number"> 
      {{ numbers }} 
    </hello> -->
  </ul>
</template>

<script>
import Fruit from '~/components/Fruit'

export default {
  components: {
    //Fruit(변수) = Fruit(import로 받은) 할당하는것을 문법상 아래와 같이 쓸 수 있음
    Fruit
  },
  data() {
    return {
      count: 0,
      fruits: ['Apple', 'banana', 'Cherry'],
      numbers: ['8','9','10']
    }
  },
  methods: {
    increase() {
      this.count += 1
    }
  }
}
</script>

<style lang="scss">
  h1 {
    color: royalblue;
    font-size: 50px;
  }
  ul{
    li{
      font-size: 20px;
    }
  }
</style>
