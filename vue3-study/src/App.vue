<template>
  <!-- 1-3. class와 바인딩 -->
  <div v-bind:class="nameClass">
    {{ name }}
  </div>

  <input v-bind:type="tmp1" v-bind:value="name">
  <button
    class="btn btn-primary"
    @click="updateName"
  >
    Click
  </button>
</template>

<script>

import { ref } from 'vue';

export default {
  setup() {
    const name = ref('junsung')
    const tmp1 = ref('number')
    // 1. class 바인딩 하기
    // 1-1. class와 바인딩 할 변수 nameClass 선언
    const nameClass = ref('aaa')
    
    const updateName = () => {
      name.value = 'junsung1';
      tmp1.value = 'text'
    };
    // 1-2. 변수 nameClass return
    return {
      name,
      tmp1,
      updateName,
      nameClass,
    };
  }
}
</script>

<style>
  /* 'name'값을 가지고 있는 변수 nameClass가 클래스에 바인딩이 되어있기 때문에 결국 클래스명은 'name'이 된다. 따라서 해당 클래스에 스타일링을 할 때에는 클래스 명을 name으로 호출해야 한다. */
  .name {
    color: red;
  }
</style>