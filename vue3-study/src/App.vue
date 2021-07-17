<template>
  <div class="name">
    {{ name }}
  </div>
  <!-- 1-4. click 이벤트 시 updateName함수가 실행되도록 한다. -->
  <button
    class="btn btn-primary"
    @click="updateName"
  >
    Click
  </button>
</template>

<script>
// 1. vue 패키지에서 reactive를 불러온다.
import { ref } from 'vue';

export default {
  setup() {
    // 1-1. 재할당이 불가능한 const 변수선언으로 name을 선언하고 오브젝트를 reactive안에 담아준다.
    const name = ref({
      id: 1
    })
    
    // 1-2. .value.id로 ref를 사용하고도 오브젝트에 접근이 가능하다.
    const updateName = () => {
      name.value.id = 2;
      console.log(name)
    };

    // 1-3. updateName함수 return
    return {
      name,
      updateName,
    };
  }
}
</script>

<style>
  .name {
    color: red;
  }
</style>