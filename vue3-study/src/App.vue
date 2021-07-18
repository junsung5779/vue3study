<template>
  <!-- 다음과 같이 v-model="name" 작성을 통해 쉽고 간편하게 양방향 바인딩이 가능하다. -->
  <input 
    type="text"
    v-model="name"
  >

  <button
    class="btn btn-primary"
    @click="onSubmit"
  >
    Click
  </button>
</template>

<script>
import { ref } from 'vue';

export default {
  setup() {
    const name = ref('junsung')
    // 함수 onSubmit 실행 시 브라우저 콘솔창에 name에 할당된 값을 출력
    const onSubmit = () => {
      console.log(name.value)
    };

    return {
      name,
      onSubmit,
    };
  }
}
</script>

<style>
  .name {
    color: red;
  }
</style>